---
title: "Resolution Problems"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by V-600 on 2007-02-14
A while back I had SUSE 10.1 installed on this computer and from memory I believe the resolution settings went to 1200*1024 (with a refresh about 65hz). 

I have been looking through the forums for help regarding raising my max resolution above 1024*768. It seems many people have this problem and the post

[http://ubuntuforums.org/showthread.php?t=361194&highlight=resolution](http://ubuntuforums.org/showthread.php?t=361194&highlight=resolution)

seemed to cover things nicely.

Following the instructions "sudo dpkg-reconfigure xserver-xorg" I went through and set my resolution to a max of 1200*1024 (and each res below). On restarting I was presented with a black screen and panic. Fortunately I found an old backup of "xorg.conf" and now am back where I started.

Pure guess work but I think the new settings made no change to the refresh rate so it tried to draw the screen at 1200*1024 and 85hz (and failed)

This time I wish to edit "xorg.conf" by hand (unless a better idea is presented) and would welcome any advice on how to proceed so as not to repeat the problem.


EDIT: Resolved problem

---

### Post by Ecthelion on 2007-02-15
Just a question -- Do you have drivers installed for your graphic card?
For high resolutions is always a good idea to have drivers installed that are more specific for your graphic card than the drivers from ubuntu.

[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)
The link refers to install on edgy, I know. But there's an also an explanation for how to install drivers for nvidia, intel and ati graphic cards.

---

### Post by V-600 on 2007-02-15
I have the nVidia drivers installed via automatix.

---

### Post by V-600 on 2007-02-15
I have solved the problem. I opened xorg.conf and incrementally increased the resolution (keeping to *xga* sizes) and now have a stable 1152*864 at 75hz

---

### Post by Ecthelion on 2007-02-15
Do you have "nvidia x server settings" in Applications > System Tools?
That's where I set my resolution. (for me its  1280 x 1024)

---

### Post by V-600 on 2007-02-15
I do have "nvidia x server settings" but there is no option to adjust resolution that i can see

---

### Post by Ecthelion on 2007-02-15
Normally there should be one...
If you open it and go to "X Server Display Configuration" The there should be "Resolution: " and then a button where you can choose the reolution.

If you really can't adjust it there it's probably because you installed it via automatix and you don't have the latest drivers.

---

