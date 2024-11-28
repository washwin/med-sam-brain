# SAM Adaptation for mp-MRI Brain Tumor Segmentation
## Deep Learning Project
## Ashwin Waghmare 210010060
### *Data acquisition*
Download Link: https://www.synapse.org/Synapse:syn51156910/wiki/627000

The dataset folder structure should be as follows:

```
-data
--brats #Adult Glioma Segmentation
--brats_ssa #Subsaharan Glioma Segmentation
--brats_ped #Pediatric Glioma Segmentation
--brats_men #Meningioma Segmentation
```

### *Set the environment*
```
conda env create -f environment.yml;
conda activate sam_adapt_brain;
```

### *Training & Testing*

**Training**

```
python train.py -net sam -mod sam_lora -exp_name drytest -sam_ckpt ./checkpoint/sam/sam_vit_b_01ec64.pth -b 1 -dataset brats -thd True  -data_path ../data -w 8 -four_chan True 
```

**Validation**

```
python val.py -net sam -mod sam_lora -thd True  -dataset brats -weights logs/.../Model/best_dice -sam_ckpt logs/.../Model/best_dice -mode Validation -four_chan True 
```