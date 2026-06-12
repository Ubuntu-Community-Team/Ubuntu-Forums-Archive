---
title: "Can't boot"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Makaze on 2007-04-04
I can't get past the ubuntu loading splash since I made a configuration change when trying to boot.

I am a total n00b when it comes to this so forgive me. I have an Acer TM6460-6752 Laptop.

I was attempting to install/configure my Labtec 5-button mouse to no avail. I followed the instructions found here: [http://www.madman2k.net/article/11/#p4](http://www.madman2k.net/article/11/#p4) as directed by another thread. Since these changes I can now no longer boot. I really am hoping to not have to format and reinstall again losing all my information on my drive.

I do have a dual boot. I can boot into windows with no problem. I have tried recovery mode and it will not boot either. I don't know if it helps but I do have a live cd.

Any help would be great. Thanks.

---

### Post by Happy_Man on 2007-04-04
I suppose you were fiddling with xorg.conf? Did you make a backup? If so, you can boot from the livecd, mount your drive, and change it back.

---

### Post by Makaze on 2007-04-04
how exactly do I mount my drive? and I'm assuming I'm just grabbing the backup on disk or from the CD?

---

### Post by Happy_Man on 2007-04-04
To mount a drive, you must first know the partition name: eg, sda1, hda2, etc. Then, once you boot from livecd, use the command

```

sudo mount /dev/(partition name) /mnt/Ubuntu

```

That gives you full access to all your files, including xorg.conf, from the loacation /mnt/Ubuntu from livecd. Then, once you've found xorg.conf, undo whatever changes you might have made, and see whether it boots.

---

### Post by Makaze on 2007-04-04
I have tried all combinations of the above code with the two possible drives that it could be and no combination has worked. It either days that /mnt/Ubuntu doesn't exist or /dev/sda6 (or whatever drive I put in) doesn't exist.

---

### Post by Makaze on 2007-04-13
ok, I finally got it mounted and the xorg restored... but I am still not able to boot.

---

### Post by dstew on 2007-04-13
Did you install the EvDev driver? The boot problem is probably related to some kernel module that is misbehaving, since you can't boot even to recovery mode. If it was due to an xorg.conf problem, you would be able to boot, but not use the graphical interface. So I think it is some other problem with your kernel and modules.

You can see exactly where the boot fails by editing the grub menu. Press 'e' when the grub menu appears. Then, select the kernel line, and remove the quiet and splash from the end of it. Press enter. Now, remove the line that says quiet by selecting it and pressing 'd'. Then press 'b' to boot. Now watch the dislpay, and it will give you messages showing how far the boot process proceeds, and we can get a clue as to why it is not successful.

---

