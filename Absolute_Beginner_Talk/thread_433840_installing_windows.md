---
title: "installing windows?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by matt_tee on 2007-05-05
how do i install windows xp alongside ubuntu?

I had a problem with windows xp and had to completely delete it.

I then installed ubuntu onto the entire 80gb disk. but i would like to partition ubuntu and install xp onto the other 40gb partition.

help?

thank you.

---

### Post by Najand on 2007-05-05
Use gparted in Ubuntu live CD. 
Resize your EXT3 partition. 
Make a new NTFS partition.
Install windows on it.
After installing it, retrive your grub using:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by cptjaben on 2007-05-05
First your going to want resize the your 80gb to make it how you want it for the install, that is how much you want for windows/ubuntu/swap. you can do this by using a live CD or gnome partition editor, which i believe you will need to install. Next boot the windows cd and install windows (make sure choose the correct partition when installing). Windows will often delete GRUB so after install if your computer now just boots to windows without letting you choose at startup you will need to run a live cd again and reinstall GRUB boot loader. This process has worked for me a few time so far, I hope that helps.

---

### Post by matt_tee on 2007-05-05
is there a step by step guide?

sorry for being a noob....:confused:

---

