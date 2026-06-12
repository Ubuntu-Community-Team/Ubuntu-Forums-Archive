---
title: "Confused about Grub"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by northicert on 2007-06-02
I installed Feisty on slave drive with master unplugged. OK..
Ran Feisty with floppy that I used in install and slave drive.  OK..
plugged in master drive that has windows XP without the disk in floppy.  OK
put disk in floppy and booted.  Was looking for Ubuntu load but it looked at floppy and gave me a GRUB and stopped.  I'm not quite sure which direction to head.  I've checked threads and they all speak of creating a floppy Grub disk but I think the commands they are using are linux commands and I'm green there.

---

### Post by H.E. Pennypacker on 2007-06-02
GRUB has its own command line interface, which you can access to use those commands.  

[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

---

### Post by oilchangeguy on 2007-06-02
> **northicert said:**
> I installed Feisty on slave drive with master unplugged. OK..
Ran Feisty with floppy that I used in install and slave drive.  OK..
plugged in master drive that has windows XP without the disk in floppy.  OK
put disk in floppy and booted.  Was looking for Ubuntu load but it looked at floppy and gave me a GRUB and stopped.  I'm not quite sure which direction to head.  I've checked threads and they all speak of creating a floppy Grub disk but I think the commands they are using are linux commands and I'm green there.

you keep saying floppy. grub, nor anything else is going to fit on a floppy. you should actually install ubuntu on a hard drive set as master. then reinstall the windows hard drive jumpered as slave.

---

### Post by northicert on 2007-06-02
Thank you.  It's going to take awhile but I think it will help.  I hope it gets me over the hump.

---

### Post by northicert on 2007-06-02
I can't reinstall windows.  I don't have a cd.  This is a preinstalled version and I don't want to lose it.

---

### Post by oilchangeguy on 2007-06-02
> **northicert said:**
> I can't reinstall windows.  I don't have a cd.  This is a preinstalled version and I don't want to lose it.

i didn't say reinstall it. re-read my previous post.

---

### Post by northicert on 2007-06-02
You're right.  You mean swap slave and maste settings.

---

### Post by candtalan on 2007-06-02
> **northicert said:**
> Thank you.  It's going to take awhile but I think it will help.  I hope it gets me over the hump.

I believe a boot floppy (which I have never actually used) using grub facilities, will need to point to the linux drive - I think yours is the second drive which grub will call drive 1 (because the first drive, drive 1, is counted as zero). Then the partition to boot from needs to be pointed to. I do not know where on your second drive the booting information is (?).

If the linux system ( '/' )(with its /boot directory included) is on the first partition, then grub will see this as (hd1,0) the second drive and its first (that is, zero) partition.

hth

---

### Post by oilchangeguy on 2007-06-02
> **northicert said:**
> You're right.  You mean swap slave and maste settings.

you are correct. that's the way i've got my computer set up. however ubuntu was installed on the master drive first. not later swaped from slave to master (that will confuse ubuntu, windows did not seem to care). i did mine like this first installed ubuntu on master drive, removed the drive, did a fresh windows install with drive set as master. removed the drive. reinstalled the master ubuntu drive, and reinstalled the windows drive jumpered as slave. works fine. grub gives the option to boot either os.

---

### Post by northicert on 2007-06-02
Ok Thanks.

---

### Post by handydan918 on 2007-06-02
If nothing else works, I would try just re-installing Ubuntu with both drives hooked up the way you want them to be used. I have never had GRUB fail to recognize a windows partition that way. If in doubt, do a full backup of your windows partition, just in case. you really should, anyway. If your data is important, i would not trust it to windows, as single harddrive, and chance!

---

