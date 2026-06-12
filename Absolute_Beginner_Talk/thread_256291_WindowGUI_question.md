---
title: "Window/GUI question"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2006-09-12
I notice when I am running ubuntu that if I grab a window and drag it around the screen I can see a tail (for lack of a  more technical term) that follows the window. Does anyone else have a similar issue?

I was at one time running windows on the same machine and never noticed this issue. Is there a setting or something i should change?

Thanks for the hlep!

---

### Post by fritz_monroe on 2006-09-12
I'm not sure if I'm right here or not, but to me it sounds like a screen refresh rate.  You could try increasing that to see it it helps.

---

### Post by rokknroll on 2006-09-12
What gfx card you using?  and do you have the latest drivers installed?  Ive only ever seen trails when i didnt have 3d acceleration and the cpu was doing the grunt work of redrawing the desktop(thats a kinda windows way to put it though).  If you have an Nvidia card, the drivers are available through synaptic, as for ati try [http://www.ati.com/products/catalyst/linux.html](http://www.ati.com/products/catalyst/linux.html)
If its not this post back with more info. :)

---

### Post by cjnkns on 2006-09-12
I have Nvidia GeForce gfx driver on my laptop.
Looking here
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

It says to install nvidia-glx I notice in my package manager only the nvidia-kernel-common is installed. Is it ok to install only the nvidia-glx since the other is already installed?

Thanks!

---

### Post by cjnkns on 2006-09-14
I installed the nvidia-glx from synaptic but I still seem to be getting the trails when dragging windows around the screen.

I also tried to run the sudo nvidia-glx-config enable command as the ubuntu dapper guide said to do but it gives me this error..

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.


Any help would be appreciated...!

Thanks!](*,)

---

### Post by cjnkns on 2006-09-14
I finally figued it out. Evidentally it helps to read the documentation all the way through BEFORE getting frustrated and posting to the forums :) who would a thunk it.#-o

---

### Post by cjnkns on 2006-09-18
I have to drudge this thread up again.
After downloading the new nvidia drivers I am still seeing the effects of trails when dragging windows... I modified the file as the ubuntu dapper guide said to chagne nv to nvidia and i see the Nvidia screen dispaly upon booting up.


Does anyone else have this type of problem? Did you fix it or do most people just ignore it?

Kind of stinks to have to live with this if it can be fixed ...

Any help is appreciated!](*,)

---

### Post by cjnkns on 2006-09-18
Nobody is familiar with this problem?  :confused:

---

### Post by IYY on 2006-09-18
Maybe you should try using XGL/Compiz? It has several disadvantages, but moving windows is 100% smooth.

---

### Post by demonoid on 2006-09-19
I had same problem this help me : 
gconftool-2 --type bool --set /apps/metacity/general/reduced_resources true

---

### Post by EddieA on 2006-09-19
I have this problem too but I put it down to a really old graphics card - also changing kernel from default 386 to 686 speeded things up a bit.
Other possibilities are graphics RAM and drivers.

---

### Post by cjnkns on 2006-09-20
what does that do?

---

### Post by cjnkns on 2006-09-20
Sorry i mean this command ?

gconftool-2 --type bool --set /apps/metacity/general/reduced_resources true

My laptop is not even a year old yet it should not have any problems at all displaying windows correclty. I did fine with Windows XP I should proably just put it back on.. and forget about it.

---

