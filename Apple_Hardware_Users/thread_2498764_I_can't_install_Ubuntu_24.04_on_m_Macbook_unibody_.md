---
title: "I can't install Ubuntu 24.04 on m Macbook unibody 5.1"
date: 2024-06-26
forum: Apple Hardware Users
---

### Post by ecebral on 2024-06-26
I have a Macbook unibody late 2008 core2duo 2,4GHz, 8Gb of RAM, Geforce 9400M 256Mb and 256Gb SSD.
I'm new on Ubuntu and linux OS. 
24.04 was installed correctly, but at boot, it remains with a black screen and a flashing dash. If I press too many keys I end up entering the Ubuntu OS.
Once inside it doesn't go very well, and when I try to install the nvidia graphics drivers with the betas through the repository in the next boot I get the nvidia logo with horizontal stripes and it doesn't work anymore.
Some help?
Sorry for my english, is not my language.

Thanks!

---

### Post by renaesmith on 2024-08-09
> **ecebral said:**
> I have a Macbook unibody late 2008 core2duo 2,4GHz, 8Gb of RAM, Geforce 9400M 256Mb and 256Gb SSD.
I'm new on Ubuntu and linux OS. 
24.04 was installed correctly, but at boot, it remains with a black screen and a flashing dash. If I press too many keys I end up entering the Ubuntu OS.
Once inside it doesn't go very well, and when I try to install the nvidia graphics drivers with the betas through the repository in the next boot I get the nvidia logo with horizontal stripes and it doesn't work anymore.
Some help?
Sorry for my english, is not my language.

Thanks!
I also have the same installing issue with Ubuntu 24.04 on my Macbook. Did you find any solution?

---

### Post by slazik on 2024-09-29
Have either of you made any progress.  I have a similar install that I would like to attempt.

---

### Post by joey-elijah on 2024-11-04
For the 9400M you'd need the 340x series NVIDIA driver, but Ubuntu dropped support for that in Ubuntu 23.10:

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/340.108-0ubuntu8](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/340.108-0ubuntu8)

The advice is to use the open-source driver (which Ubuntu 24.04 LTS will use by default). Or you could install/try Ubuntu 22.04 LTS instead - it's supported until 2027, and Snaps and Flatpaks mean you can get the latest apps etc. 

If you want/need Ubuntu 24.04 LTS then there is a community-made legacy NVIDIA drivers PPA. This is totally unofficial, but moderately popular with users with older GPUs. That could be worth trying, but only if you're aware of the risks. Anecdotal reports suggest that 340.x drivers don't work on kernels newer than v5.18, but the PPA lists instructions on a few config files edits which are said to get the drivers working properly.

But it's a fair bit of effort if you're new to Ubuntu - newer devices do tend to 'just work'. 

If you can get it working there are some other tweaks you will need to make as you're on a MacBook, i.e., to get brightness keys working but those are trivial enough and there's plenty of YouTube videos and blog how to's on those. Also, make sure to use the Xorg session (select from the cog on the login screen) as Wayland doesn't work well (if at all) on older NVIDIA GPUs.

If all that fails, don't throw the laptop away as there's OCLP - an open source mac tool that patches newer versions of macOS to run on older, unsupported devices. It's fairly easy to use. I use it to keep my old 2012 MacBook Pro (dual-boots Ubuntu, don't panic anyone :P) useful. It's running the latest *Sequoia* release without any major issues.

---

