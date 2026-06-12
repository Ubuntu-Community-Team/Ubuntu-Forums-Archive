---
title: "ubout the updates"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-29
1.not directly ubutnu updates but ALL the programs I've installed on ubuntu.
for example - I've installed blender 3d version 2.41
but version 2.42 is out for a month already - why do I have to go directly to the blender3d.org site to download the program rather then get the direct update from update manager or from synoptic ?
doesn't it supposed to find the updates for me ?
I have about a hundred programs installed and I can't go to every site to download the new version.
2.when I download a new version , it's a zip2 file - so it doesn't "install" the program but exctract the program to a folder , it's workable but it doesn't install it.
how can I install a program from the zip2 file ?
3.I got yafaray version 0.0.8 installed on ubuntu , but version 0.0.9 is out already , I've downloaded the .deb file , but when I try to install it it says that it need "libc6" in order to install
I've got it already - but I still get the error
how can I install yafray 0.0.9 ?

thanx ahead

---

### Post by mscman on 2006-07-29
The Ubuntu repos are not always kept 100% up-to-date. The reason for this is that many times new releases aren't exactly stable and some require major system changes just to work (i.e. your libc6 error when trying to update yafray). As far as installing a program from .zip2 archives, you should look for a README file either in the .zip2 archive or on the Blender3D website.

Many times the "latest and greatest" version of software isn't much of an improvement over the previous version, especially if it's not a major release. If it really is worth having, wait a few weeks and it should be in the repos (assuming you don't want to go through the hassle of compiling/installing manually) :)

---

### Post by lafnlab on 2006-08-12
I'm very big on Blender and I've been waiting for Ubuntu to upgrade this. However, i got tired of waiting as there are some new features in Blender 2.42a that I really wanted to try out. To me, it was important enough to grab blender and install it on my own (I grabbed the static version, not the dynamic version) 

I tried to install Yafray 0.0.9 with the same problem. However, I don't use Yafray often enough to care that much about it. I kept the Ubuntu version of Blender and Yafray installed, just in case. 

BTW, you can have multiple version of Blender on your system if you want. When I was using Slackware, I just kept the different versions in separate directories in my /home/lafnlab directory.

---

### Post by MaximB on 2006-08-13
yeah - I did it to
but the 42a version isn't really installed
I've just exctracted it to a folder
but it works great
I have a LOT to learn about it
tried using some effect - cool stuff
not evrything I managed to do
 
like when I apply weight to the corners of the mesh and add soft body it still falls down and the corners don't stay still
and I didn't managed to make a cube "solid" so when the mesh falls it won't go tru the cube , but fall on it.
 
can you help me with that ?

---

### Post by paris_m_ on 2006-08-31
Read this thread: [http://www.blender3d.org/forum/viewtopic.php?t=9285]("http://www.blender3d.org/forum/viewtopic.php?t=9285")

You can find there a deb package of blender 2.42a, built for dapper. For yafray I think it's better to compile from source.

---

