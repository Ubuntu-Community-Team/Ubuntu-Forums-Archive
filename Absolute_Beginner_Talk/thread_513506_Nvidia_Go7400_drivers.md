---
title: "Nvidia Go7400 drivers?"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by TearJacK on 2007-07-30
Hello

trying to get 3D accelaration in Ubuntu 7.04
using the standard "nv" in ubuntu now.

but how can i get it to work?
where can i find the drivers
and how to install, 

i use Ubuntu 64bit and my gfx card is GO7400
thanks for all the help, ive struggle with is for along time...

thanks on advance

---

### Post by Redache on 2007-07-30
The IA64 drivers should work fine.

Are you sure you're downloading the 64 bit drivers and not the 32 bit ones?.

---

### Post by TearJacK on 2007-07-30
i dont know where to download them
can you give me a direction?

---

### Post by Redache on 2007-07-30
Try [[COLOR="Indigo"]Envy[/COLOR]]("http://www.albertomilone.com/nvidia_scripts1.html")

It auto installs the right drivers so hopefully this will work for you.

i don't have Feisty installed on this computer at the minute (Playing with Fedora) so i can't search the Repo for you.

Although if you want to try using the repo's for it do a 
```
sudo apt-cache search nvidia 64
```


Sorry that i can't give much more help than that.

---

### Post by Hospadar on 2007-07-30
There are two places to go to get nvidia drivers, you can either get the from the package repository or from nvidia's website

From the repository:
go to System->Administration>Synaptic Package Manager
Search for "nvidia"
Select and install the "nvidia-glx" package EDIT: this might be a different package for 64 bit, read the description, it should be relatively obvious which system it is for. (right click, mark for installation, apply), there are some instructions in the description of the package for how to enable the drivers after you install them (something along the 
lines of "sudo nvidia-glx-configure enable" in the command line)

From nvidia's website:
go to [http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp) and select the drivers you need (geforce 7 series, linux x86 or x64 depending on which version of ubuntu you are running) there are some instructions on the nvidia website for how to install these, but to give you a basic run down:

first do ctrl-alt-F1 to get a text terminal
first, make sure you have build-essential installed:
```
sudo apt-get install build-essential
```
then do 
```
sudo /etc/init.d/gdm stop
```
this will stop your window manager so you can install the drivers
then, cd to where you downloaded the drivers, probably something like
```
cd ~/Desktop
```
then use "sh" to run the drivers
```
sudo sh <Name of the drivers you downloaded>
```
this will take you into a little dialog with the nvidia drivers, after that's done, you can either restart your machine, or just restart your window manager
```
sudo /etc/init.d/gdm start
```
you may have to do a ctrl-atl-F7 to get back to the virtual terminal where the window manager is.

As you can tell, the first option is a little easier, I would start with that, it's the same software.

Hope this helps.

---

### Post by TearJacK on 2007-07-30
Thanks a bunch guys!

the guide from Hospadar workd!

thanks again.

now on to getting Compiz Fusion to work!

---

### Post by TearJacK on 2007-07-30
hmm strange prob here, the line over windows (where you press the x to close)
is gone... i cant move or close windows..

---

