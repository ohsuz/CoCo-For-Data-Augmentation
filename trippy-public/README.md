


## TripPy: A Triple Copy Strategy for Value Independent Neural Dialog State Tracking

This code is an adaptation of its [**original implementation**](https://gitlab.cs.uni-duesseldorf.de/general/dsml/trippy-public).   Here, we only include its training on whole MultiWOZ dataset and its re-training for CoCo-generated data.
## Data
[**Download**](https://storage.cloud.google.com/sfr-coco-dst-research/trippy-public-resources/data.zip) MultiWOZ data, 
 uncompress it, and place the resulting ```data``` folder into the current directory (```coco-dst/trippy-public/```).

## Train baseline
Run the following command to launch the baseline model training:
```console
❱❱❱ sh train_baseline.sh
```
After training the model, modify ```MODEL_CHECKPOINT``` in line 50 of ```interface4eval_trippy.py``` to the path of the 
checkpoint you want to do evaluation. You can also [**download**](https://storage.cloud.google.com/sfr-coco-dst-research/trippy-public-resources/baseline.zip) 
the pre-trained checkpoint we used in our paper.

Then, you can simply evaluate the desired TripPy model checkpoint on CoCo-generated examples by running
```console
❱❱❱ sh run_eval.sh
```
after setting the required arguments as instructed under section ```Run Evaluation on CoCo Examples``` in 
```../coco-dst/README.md```.


## Re-Train with Multi Round CoCo Augmentation
Before running the re-training script, make sure that 
- You generated the data using multi-round augmentation with CoCo for re-training (see further details under section 
```CoCo+ multiple round data augmentation``` in ```../coco-dst/README.md``` of this branch.
- You moved the data for re-training into ```../coco-dst/coco_data```.  

Then, run
```console
❱❱❱ sh train_coco-aug.sh
```
after setting ```aug_file``` to the path of the retraining data. By default, it points to the 8x CoCo augmentation file 
that you can [**download**](https://storage.cloud.google.com/sfr-coco-dst-research/coco-dst-resources/coco_data.zip).

You can also [**download**](https://storage.cloud.google.com/sfr-coco-dst-research/trippy-public-resources/coco-vs_rare_8times.zip) 
the checkpoint we retrained with 8x augmentation reported in our paper. 


## License
The code is released under the Apache License - see [LICENSE](LICENSE.txt) for details
