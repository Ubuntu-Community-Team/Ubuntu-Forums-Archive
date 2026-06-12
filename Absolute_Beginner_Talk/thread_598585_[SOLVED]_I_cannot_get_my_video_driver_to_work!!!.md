---
title: "[SOLVED] I cannot get my video driver to work!!!"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by atlascomplete on 2007-10-31
I am getting really frustrated with this thing.

I am trying to install the NVidia driver for my HP DV6000 laptop. It has a GeForece 8400 GS video card and I downloaded the "NVIDIA-Linux-x86-100.14.19-pkg1.run" but I can't run it. I have been reading this thread: [http://ubuntuforums.org/showthread.php?t=597262&highlight=nvidia+driver](http://ubuntuforums.org/showthread.php?t=597262&highlight=nvidia+driver)

This is what happens when I try the command:

```
sudo ./NVIDIA-Linux-x86-100.14.19-pkg1.run
```

It comes back with this:

```
sudo: ./NVIDIA-Linux-x86-100.14.19-pkg1.run: command not found
```

Also, when going to the Restricted Devices Manager and clicking on NVidia, it gives me the error:
-The software source for this package: "nvidia-glx-new" is not enabled.

I have also tried installing envy, as I have heard that is helpful, but then I get the error code:
-"Error: Dependency is not satisfiable: xserver-xorg-dev"

Please help a Linux newb out!!!

---

### Post by nest on 2007-10-31
```
sh NVIDIA-Linux-x86-100.14.19-pkg1.run
```

---

### Post by carlosjuero on 2007-10-31
For the restricted driver message - make sure you have enabled Ubuntu to use available restricted drivers (Should be System Menu->Administration->Restricted Drivers Manager).

Then, as the person who replied right before me said, you need to specify 'sh' to run the install package.

---

### Post by atlascomplete on 2007-10-31
> **carlosjuero said:**
> For the restricted driver message - make sure you have enabled Ubuntu to use available restricted drivers (Should be System Menu->Administration->Restricted Drivers Manager).

Then, as the person who replied right before me said, you need to specify 'sh' to run the install package.

Yeah, but as mentioned before, when I go to the Restricted Drivers Manager, when I try to enable it, it gives me the error: "he software source for this package: "nvidia-glx-new" is not enabled." I don't know what to enable though.

So I used the command:

```
 sh '/home/atlas/Desktop/NVIDIA-Linux-x86-100.14.19-pkg1.run'
```

And it starts to run the driver program, which is good, but it then states "You appear to be running an X server. Please exit X before installing."

---

### Post by nest on 2007-10-31
> **atlascomplete said:**
> And it starts to run the driver program, which is good, but it then states "You appear to be running an X server. Please exit X before installing."

```
ctrl + alt + erase-tab
```

then

```
ctrl + alt + F1
```

then install  the drivers.

---

### Post by Keith_Burton on 2007-10-31
Atlascomplete, without intending any offense at all, I want to suggest you not proceed farther down this path. The solution to "Please exit X before installing" is to turn off the graphical interface completely, and do the whole process in cmdline only. 

A trivial typo in that mode could make it so Gnome won't start again...and then what are you going to do? Getting a broken GUI running again can be really hard for a linux newbie, even assuming you have another computer sitting there you can use to ask for help.

My own recommendation is to concentrate on getting the restricted manager driver working, and letting it install the nvidia driver for you. Maybe start a nestart a new thread titled, "nvidia-glx-new is not enabled".

Sadly I'm an ATI user and haven't run into this particular problem, but hopefully someone will be able to help out.

Best of luck!

P.S.  A quick search directed me here: [http://ubuntuforums.org/showthread.php?t=580390](http://ubuntuforums.org/showthread.php?t=580390)   and here: [http://ubuntuforums.org/showthread.php?t=580390](http://ubuntuforums.org/showthread.php?t=580390)
Maybe it'll be that simple.

---

### Post by atlascomplete on 2007-10-31
Both of those threads directed me to the same one, and the creator edited his response so all I saw was how to edit 3D effects.

I believe not all the packages were installed correctly. I'm gonna retrieve my Live CD and reinstall them.

---

### Post by atlascomplete on 2007-11-08
I got it to work. For all those that are reading this thread for further knowledge, I made sure that in the Add/Remove programs list it allowed to retrieve packages from the internet. From there I installed the necessary NVidia packages.

Kick-a. Thanks guys!

---

### Post by Maestro23 on 2007-11-08
> **atlascomplete said:**
> I got it to work. For all those that are reading this thread for further knowledge, I made sure that in the Add/Remove programs list it allowed to retrieve packages from the internet. From there I installed the necessary NVidia packages.

Kick-a. Thanks guys!

Good deal man.  Please mark this thread SOLVED using the THREAD TOOLS.

Thanks.:)

---

