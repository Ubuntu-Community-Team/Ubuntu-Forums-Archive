---
title: "3D renderes: need your help"
date: 2008-01-23
forum: Art &amp; Design
---

### Post by nephritiri on 2008-01-23
hey.. for those who are dealing with volume graphics... can you help me out here?

im currently rendering regular-shaped objects like boxes... 
iv had the space dimension x*y*z and the resolution/voxel density of N voxels/cubic centimeter...

now... i counted the voxels occupied in the space by the rendered object... T voxels...

now... i want to know its equivalent measurement in cubic centimeters in the REAl world... how should i do that? am i missing an important data here? please help... im new to volume graphics...

---

### Post by Gannin on 2008-01-24
Wouldn't you decide that yourself?  I mean, wouldn't you create your own scale?  For instance, saying that one voxel is equal to one cubic centimeter, and then build everything according to that formula so it all ends up in the scale you want.

---

### Post by nephritiri on 2008-01-24
thanks... the very simplicity of these math calculations makes me confused. i think that im getting there to solving it, it's just that im being confused by the results that i get...

ahm... lemme giv an example.

i hav a space of 267x200x267 voxels...
now, let's say that the rndered object occupies 3,146,401 voxels...
i set a voxel density of ... 28.346 voxels/cubic cm

? cubic cm = 3,146,401voxels/(28.346voxels/cm^3)
that yields 110,999.8236cm^3..

but precomputing the real-world object has dimensions of only 21cmx12cmx31cm = 7,812cm^3...

so, i know that i was wrong in setting the voxel density.
having precomputed the real-volume, i should be able to get the voxel density...
1cm^3 = 3,146,401 voxels/(7,812voxels/cm^3)

that yield 402.765105 voxels/cm^3

now, my problem is... im computing volumes of different sample objects...
how can i set the correct voxel density without precomputing the real-world volumes?

honestly, i feel stupid... this should be easy... i just don't get it. need you to enlighten me.
thanks.

---

