---
title: "[SOLVED] External Drive"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by ibbill on 2007-10-30
I have a NST-350u2 Nexstar external hard drive. Have downloaded the latest drive only one I can find is for windows 98. GRRR  Not sure what I am missing any help would as usual will  be greatly appreciated Again

---

### Post by Inxsible on 2007-10-30
> **ibbill said:**
> I have a NST-350u2 Nexstar external hard drive. Have downloaded the latest drive only one I can find is for windows 98. GRRR  Not sure what I am missing any help would as usual will  be greatly appreciated Again

What are you trying to do again?

mount the drive? IF so, you do not need the windows drivers at all. just plug in the drive and see what happens. What is the file system on the drive?

---

### Post by Inxsible on 2007-10-30
Also, unless you actually have 4 different CD drives (which I highly suspect) you can remove the corresponding entries for the drives from fstab and then it will only mount the actual drives.
```
gksudo gedit /etc/fstab
```

---

### Post by ibbill on 2007-10-30
Sorry  did  not give you   enough info I will try again oops 

I have 2 internal drives on my computer each has 2 partitions. first drive has xp pro Sp1and Gusty installed

2nd drive has xp home sp2  plus vista home premium.

I have a external drive that has 2 partitions on it and it has data on one partition and pictures and videos on the other.

Now I had to take this external drive to my daughters and copy some videos over to her computer.

When I came back and plugged it back in the external drive was not found also I booted up to windows xp home grr hate going there now lol  and drive not found.

Why that would happen not sure never happen before when I removed it and the rehooked it up it was always detected.

Hope this helps sorry not enough info to start with.

---

### Post by Inxsible on 2007-10-30
Did you happen to drop the drive on the way? Maybe some physical damage.

---

### Post by dfreer on 2007-10-30
The reason why you can't find a windows driver, except for a windows 98 driver, is that even in a windows enviroment, a driver should not be needed for a external hard drive. The windows 98 driver is probably a USB driver, which windows 98 needs to use USB devices correctly.

In a linux enviroment, you can't expect to use windows drivers to accomplish anything (except in the case of using ndiswrapper with broadcom wireless cards). It's not windows, it's linux.

EDIT: It may be that it is not mounting at the usual place, this can happen when another USB drive has been added, or sometimes on my server I can see an external get assigned /dev/sdd, and then get unplugged. when it is plugged back in, it gets assigned /dev/sde. But I would need more info to be able to help you, like the output of these commands:
```
sudo fdisk -l

cat /etc/fstab

cat /etc/mtab

ls -l /media/*
```

---

### Post by ibbill on 2007-10-30
OMG heres what I did I have to usb ports on the back of my computer. I moved the external drive usb plug in to the other usb slot.

Presto they reappeared. Not sure what or why maybe the driver is on that port only crikey.  Also booted up to windows xp home sure enough shows there also. Now i have two on here that I have no idea what they are.cd rom 1 or cd rom 2

When I click on the cd rom 1 or cd rom 2 unable to mount. How can I remove them.

---

### Post by ibbill on 2007-10-30
oops sorry I'm losing it here note pluged my web cam in the usb port where the external drive did not work but the web cam does.

---

### Post by ibbill on 2007-10-30
Inxsible should I remove the 2 that I  hi lighted and then save the page.

---

### Post by ibbill on 2007-10-30
Inxsible and defreer thank you ever so much for your help just awesome. Marking this thread solved thanks again for you time effort and help 

Bill

---

