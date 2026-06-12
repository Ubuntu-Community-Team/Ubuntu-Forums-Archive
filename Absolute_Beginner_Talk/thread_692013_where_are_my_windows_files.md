---
title: "where are my windows files"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by shumboom on 2008-02-09
Hi

Real newbie here. I just loaded ubuntu 7.1 in a dual boot configuration. Now I would like to find my mp3 files and videos on windows xp to check out if everything works. Where are they? I can only see my linux partition.

Also what is the equivalent of device manager on ubuntu? Im not sure if it found my graphics card or not. 


Lastly  I would like my maximise window to cover the whole screen - any chance of that?

thanks,Shumit

---

### Post by taurus on 2008-02-09
If you didn't install Gutsy over your XP, it should still be there.  You just need to mount it first before you can access it.  Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That would be upper case letter L.

And if you want to see if there is a driver for your graphic card, go into System -> Administration -> Restricted Drivers Manager to see if it's on the list and then install a driver by clicking the enable for it.

---

### Post by codeslicer on 2008-02-09
The Device Manager can be accessed from System->Preferences->Hardware Information. Go to Places->Computer to see if you can mount some drives

---

### Post by shumboom on 2008-02-09
Hi , I tried that but got the following: - not sure why it claims I have put in two dashes. I found the device manager, thanks S

----------------------------------------------------------------
shumit@Pinku-Hp:~$ sudo fdisk -L
fdisk: invalid option -- L

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
shumit@Pinku-Hp:

---

### Post by halitech on 2008-02-09
try

sudo fdisk -l (lowercase L) and it should work

---

### Post by shumboom on 2008-02-11
thanks all, I followed a link here which found my windows files and setup my sd card reader

[http://www.linuxforums.org/forum/xandros-help/111328-help-sd-card.html](http://www.linuxforums.org/forum/xandros-help/111328-help-sd-card.html)

Im a bit disappointed that Ubuntu couldnt mount my windows files automatically - makes it diffcult to convert my parents to linux!

---

### Post by oedha on 2008-02-11
really.....after you mount them...did you put the syntax on fstab ?
if you can mount them...means you can also make it auto mount

---

### Post by BatsotO on 2008-02-11
you can mount any partition automatically, you'll need to configure your /etc/fstab so the system will mount your windows partition on boot. [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

I hope this will help.

---

### Post by jan quark on 2008-02-11
you can automount them editing the fstab file

post the result of 
```

sudo fdisk -l
```

and

```
cat /etc/fstab
```

thank you

---

### Post by shumboom on 2008-02-11
I have automounted them now - i just think its a bit of effort for anyone over 65

thanks for all the help,Shumit

---

### Post by SunnyRabbiera on 2008-02-11
> **shumboom said:**
> I have automounted them now - i just think its a bit of effort for anyone over 65

thanks for all the help,Shumit

this happens sometimes during dual boot so I am not surprised of your issue...

---

