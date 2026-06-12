---
title: "Unistalling Ubuntu"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Svenhook on 2007-09-16
Alright so here's the situation. I downloaded and installed linux but being the moron I am, I downloaded the server edition which apparently doesn't have X. So I need to get this completely off of my computer so I can install the pc edition. Unfortunately I cant just wipe the harddrive cause its got vista and all my stuff on it and it would be a big time consuming hassle to do this so what should I do and how should I go about doing it? Thanks!!

---

### Post by peabody on 2007-09-16
don't worry about wiping it out, just download the desktop live cd and install from that, using the partitions you set aside for the server install.

---

### Post by dwhitney67 on 2007-09-16
Install the distro you want, and partition exactly like you did it before.  The new Linux distro will wipe out the existing one.

---

### Post by st33med on 2007-09-16
Download and burn the Gparted Live CD from [here]("http://gparted.sourceforge.net/livecd.php"). Boot from the CD and erase your partition. Then, create a ext3 partition of the same size. Also, erase the extended and swap partition.

---

### Post by w4ett on 2007-09-16
Before you jump the gun, try this:

From the command line:

```
sudo apt-get install gnome-desktop
```

This will complete the gnome gui installation 

HOWEVER, to install the desktop edition, just pop in the live cd and let'er rip...no need to uninstall

Good Luck

---

### Post by Svenhook on 2007-09-16
Thanks a lot for the help! I figured id have to unistall cause i tried just installing edubuntu and got the tty error thing and everyone seems to say the problem is that you have to wipe the drive. Ill burn a new live Cd and try again. Thanks again

---

### Post by Svenhook on 2007-09-17
So this is where I am now. I downloaded and made a disc of Xubuntu. I booted it up and am currently just running it off of the disc. I decided to do the full install and began the process formatting the partition that the other Linux installation was only just to cover it up as suggested. Well, after 70% of the installation it gets an error message saying that I need to make a new livecd (burn it at a slower rate?). Here is where it gets tricky. If i restart without the livecd it goes to GRUB and gets an error because the boot record thinks Ubuntu is installed but the partition was formatted. So i can't get back into windows to re-download/burn the cd. The only OS i can run is Xubuntu from the CD which means none of my drives are noticed. Any ideas on what I should do, or to get me into windows?

---

### Post by w4ett on 2007-09-17
Pop your vista disk into the drive, boot to a recovery console and let it fix the windows mbr...you should then be able to boot into window normally.

---

### Post by Svenhook on 2007-09-17
I gave it a shot and no luck. It wouldnt boot into recovery mode and when i used the actual vista disc it only gave me the option of completely reinstalling it which I would like to avoid at this point. Is there anyway I can download and burn to disc Xubuntu from the disc Im currently using?

---

### Post by w4ett on 2007-09-17
When you run the windows disk it will detect the current install of windows and ask if you want to repair instead of install....

---

### Post by Svenhook on 2007-09-17
It didn't. It just went striaght to the install process. Ill try it again, but I don't think its working out that way for some reason.

---

### Post by w4ett on 2007-09-17
an in-place reinstall won't hurt anyway...all your data in the ntfs partition will remain there.

---

