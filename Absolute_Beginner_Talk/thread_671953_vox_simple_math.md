---
title: "vox: simple math"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by nephritiri on 2008-01-19
hey there everyone. i need your help on correcting me in my computation.

this may be a little off-topic, but i dont know where to put this thread. this is more on graphics...but here it goes.

i made a program on rendering a 3D object from a series of 2D binary images using C++. now, one thing i need to do is compute the volume occupied by the real-object iv taken picture of (the object of interest in the 2d images) by using the the number of voxels of the rendered 3d volume.

i precomputed the real-world object and these are the dimensions:
            w = 21 cm
            h = 12 cm
            d = 31 cm
            V = 7,812 cm^3

these are the given:
            space dimensions(w x h x d): 267 x 200 x 267 
            total voxels tVox = 14,257,800
            (btw, i based the space dim on the img dim: 267x200)


1.) get the number of voxels occupied by the 3Dobj(the rendered one). i got 799,825. now, i can say that 799,825 voxels occupy the the 7,812 cm^3 in the real world.
     
2.) from these, i can get how many  voxels occupy 1cm^3.
      1 cm^3 = (799,825voxels/7,812cm^3) = 102.38 voxels 

3.) to check, i compute the how many cm^3 is 799,825 voxels
       (799,825 voxels/102.38 voxels) = 7,812.32 (almost 7,812 cm^3)

4.) now that i know how many voxels are there in 1cm^3 and i want to know the space dimension in cm^3, what i did was (14,257,800/102.384) = 139,258.0872 cm^3

now, i want to compute the volume of another real world object,
given the same space dimensions above. i can compute it without precomputing it right? i jz hav to divide the total voxels occupied by the rendered obj by 102.384 to transform the measurement in cm^3, right?

(btw, everything is just estimates, so little errors are tolerable)

please if you have any suggestions on how i can write or explain this more formally, just tell me.

im hoping for your response. thanks.

---

