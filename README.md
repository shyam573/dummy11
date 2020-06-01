
# Monodepth2 training with roll angles:

## Procedure:

- Roll angles are varied in between a range of -30 degrees and 30 degrees with a uniform distribution.

- The random degrees that are selected for increment or decrement is in between 0.08 and 0.14 with uniform distribution.

- For a sequence of images, when a random angle is generated, angles are incremented or decremented with random degrees for each image processed only once.

- Increment or decrement of angles is continued in steps of random degrees till the random angle is obtained and then vice versa is performed in steps of random degrees till zero is obtained.

- For a new image sequence, the roll angle again starts from zero.

- Random angle is generated again and the above steps are repeated for all image sequences.

- This entire procedure is offline. The zoom factor suitable for this approach is 1.75. Zoom factor is obtained based on trial and error method such that remove all black pixels at edges are removed, hence the image is corrected. The flag used of rotation is `cv2.INTER_LANCZOS4` and for resizing is `cv2.INTER_LINEAR`.

## KITTI Benchmark:

All the evaluations are done using median scaling on KITTI dataset.


| --model_name | abs_rel | sq_rel | rmse | rmse_log | delta<1.25 (a1)| delta<1.25<sup>2</sup> (a2) | delta<1.25<sup>3</sup> (a3) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| mono_640x192_no_roll        | 0.117 | 0.902 | 4.897 | 0.194 | 0.872 | 0.958 | 0.981 |
| mono+stereo_640x192_no_roll | 0.108 | 0.820 | 4.693 | 0.188 | 0.884 | 0.961 | 0.981 |
| mono_640x192_original       | 0.115 | 0.903 | 4.863 | 0.193 | 0.877 | 0.959 | 0.981 |
| mono_1024x320_original      | 0.115 | 0.882 | 4.701 | 0.190 | 0.879 | 0.961 | 0.982 |
| **mono_640x192_roll**       | **0.146** | **0.995** | **5.592** | **0.225** | **0.800** | **0.942** | **0.977** |


## Inference results:

The results are not satisfactory.


#### No angle:

![alt text](images/out_image_angle_0.jpg)

#### +5 degrees:

![alt text](images/out_image_angle_5.jpg)

#### +10 degrees:

![alt text](images/out_image_angle_10.jpg)

#### +15 degrees:

![alt text](images/out_image_angle_15.jpg)


#### +30 degrees:

![alt text](images/out_image_angle_30.jpg)


#### -5 degrees:

![alt text](images/out_image_angle_-5.jpg)


#### -10 degrees:

![alt text](images/out_image_angle_-10.jpg)
