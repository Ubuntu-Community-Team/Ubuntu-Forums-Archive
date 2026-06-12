---
title: "setting up a dual boot system......"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-11-26
Hello all......

Just a question about dual booting.
i use 2 hard drives, one with windows xp on it and the other with gutsy, now ive just had to re-format the xp drive, and im wondering if there is a way to set up the dual boot options, with out having to re-install gutsy (thats the only way i know how to do it) so that i can select which os to start once grub has loaded. (you get a little options like screen, where you can select to run ubuntu or xp, or the recovery mode etc etc )
cheers

---

### Post by rsambuca on 2007-11-26
You can just re-install grub from any liveCD.

---

### Post by techno-mole on 2007-11-26
daft question, but how do you go about re-installing grub from a live cd ?
is it a case of booting the system with the disc or just putting it in the disc drive ?
cheers

---

### Post by mahiyar on 2007-11-26
Hopefully this link will give you all the answers, however be careful to tread carefully and take necessary precautions like backing up your data before proceeding [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by kaiju on 2007-11-26
if you need to reinstall grub:

you boot from the livecd. then, using a terminal, do
```
sudo mount -t ext3 /dev/hda4 /mnt
sudo grub-install –root-directory=/mnt hd0
sudo umount /mnt
```

of course you replace /dev/hda4 with your linux root partition (you can locate it with sudo fdisk -l), and change the -t ext3 accordingly, if you're using a different filesystem.

buuut...
if you had your windows install on another drive anyway, can't you just reinstall your windows with only that one drive connected? assuming that your grub is on the linux drive and drive names don't change, it should work as if nothing had happened. please someone correct me if i'm wrong here.

---

### Post by techno-mole on 2007-11-26
> if you had your windows install on another drive anyway, can't you just reinstall your windows with only that one drive connected? assuming that your grub is on the linux drive and drive names don't change, it should work as if nothing had happened. please someone correct me if i'm wrong here.
this is correct, but for some reason even though the bios is set to boot from the western digital hard drive (where ubuntu is installed) it boots from the samsung hard drive (where xp is installed) the only way i can get ubuntu to boot first is to hit f12 and select the drive from the list.
I did install with only the xp drive hooked up (to avoid trashing the linux drive) and ive gone from the 64 bit version of xp to normal 32 bit, and although in grub it says xp pro 64 bit version it will still boot the xp drive, but im stuffed if i can get it to boot from the linux drive, which is why ive been messing with grub.
cheers.

---

### Post by Bigbird999 on 2007-11-26
Are your 2 drives on the same IDE channel or are they on separate cables?  If I am not mistaken, The reason it is booting to the windows drive is that, in the BIOS, it is set to boot from the first hard drive it finds with a valid OS.  It is finding windows on the first hard drive (IDE 0??) so it doesn't look any further.  Not sure, but if you set your boot priority, in the  BIOS, to the second (Linux) drive, it will find the grub and give you a choice of which OS to boot.

BB

---

### Post by kaiju on 2007-11-26
could it be that this also has to do with which device is set to master? i mean it would be logical that without any extra bios settings, the bootable part from the master drive gets initialised...

---

