---
title: "Install on virtualbox os x"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Niklas_cph on 2007-05-18
Im trying to install ubuntu on vitualbox on my macbook.
But i don't have the courage to go through with step 7 (formatting). The thing is that i am not shure wether ubuntu is going to format the image allocated to it by virtualbox or my hd in general. 
Any of you guys know anything about this?

---

### Post by starcraft.man on 2007-05-18
Uhhhh.... its impossible for a virtual machine of any kind (virtual box included I suppose though I've never used it myself) to reach outside of its container and reformat your entire harddrive. The basic premise of any virtual machine is that it generates a virtual environment emulating all pieces of hardware needed with the software and you make a file of preallocated (in VMware for instance the files are labeled vdmk I think) and thats all the space the machine will have access to, if you fill it up you'd have to increase it. I wouldn't be worried about it, I would make sure to read virtual boxes documentation though. 

I've installed at least 50 different virtual machine guests and never screwed up my main OS, maybe the software but not your main OS/physical partitons.

Just curious but why do you want Ubuntu in a virtual machine?

---

### Post by miggols99 on 2007-05-18
It will just use the image created by VirtualBox. There's nothing to worry about. It's all "inside" the program. It doesn't touch your files and programs. Unless you tell it to. But you probably won't need to.

---

### Post by lazyart on 2007-05-18
If you're running in a virtual machine, ubuntu only has access to the space you allocated within the virtual machine.

---

