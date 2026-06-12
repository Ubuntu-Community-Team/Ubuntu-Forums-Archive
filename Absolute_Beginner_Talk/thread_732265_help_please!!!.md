---
title: "help please!?!?!?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by prophetk on 2008-03-22
Ok I am newer to Ubuntu and I am having a problem.  I have a Seagate Momentus 5400.3 internal laptop hard drive in an external case.  I have it powered on properly, but my computer does not see it anywhere.  (oh i run feisty fawn)  Any ideas on how to get it to see my hard drive?  I checked all over the seagate website but they don't have any support for using this as an external drive though it came with the usb cables and external case to do so.  

Thanks in advance!!

---

### Post by overdrank on 2008-03-22
> **prophetk said:**
> Ok I am newer to Ubuntu and I am having a problem.  I have a Seagate Momentus 5400.3 internal laptop hard drive in an external case.  I have it powered on properly, but my computer does not see it anywhere.  (oh i run feisty fawn)  Any ideas on how to get it to see my hard drive?  I checked all over the seagate website but they don't have any support for using this as an external drive though it came with the usb cables and external case to do so.  

Thanks in advance!!

Hi and if the drive is powered on then you can try these commands to see if it is recognized
```
lsusb
sudo fdisk -l 
``` that is a lower case L

---

### Post by waspbr on 2008-03-22
go to terminal and type:

```
lsusb
```

post the result

---

### Post by prophetk on 2008-03-22
ok it says that it can see it, but it says 

disk /dev/sdb doesn't contain a vaild partition table

so what next??

---

### Post by prophetk on 2008-03-22
Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

this is what it gave me in the terminal

---

### Post by Darganot on 2008-03-22
have you formatted the disk yet (i.e. is it brand new out of the box)?  If not, What kind of partition is on the drive?

---

### Post by prophetk on 2008-03-22
it is brand new and other than in the terminal, the computer does not see it at all...

---

### Post by Darganot on 2008-03-22
Go into 

System -> Administration -> gParted (or partition editor)

you should see all the drives available.  if you don't see your drive (it will probably be shaded out showing no partitions) try refreshing under the gParted menu.  A listing of the devices here can show you what's being seen and what's not also.

You can use this program to create a partition of whatever file system you prefer.

---

### Post by prophetk on 2008-03-22
ok i got it formatted to FAT32 since for now its going to have to work with muliple os's.  but it still is not showing up anywhere other than in gparted... is that right or is there more i need to do?

---

### Post by Darganot on 2008-03-22
I have to be honest I don't know much about external HDD's but something like a flashdrive will open up a window automatically when connected.  

You should at least be able to access the drive in Nautilus.  If you can't do that you're not done.  :)

---

### Post by saj0577 on 2008-03-22
You most likely will still need to mount it.

Try unplugging it and pluging it in again.

If not then il find the guide on mounting for you ;)

Saj

---

### Post by prophetk on 2008-03-22
thanks!  between the two of you i got it working!  much much appreciated!!!  :D

---

### Post by MadMedis on 2008-03-22
> **Darganot said:**
> I have to be honest I don't know much about external HDD's but something like a flashdrive will open up a window automatically when connected.  

You should at least be able to access the drive in Nautilus.  If you can't do that you're not done.  :)

There's a chance that it will recognize the drive and partition but not mount it automatically.  If that is the case, you will see it in the Computer screen.  Go to Places -> Computer, and look for the drive there.  It may be a good idea to switch to "List" view (look in the upper right-hand corner of the screen for this setting), which displays more information about each drive.  Simply double-click the drive's icon, and if it is not already mounted you will get a message saying something to the effect of "Mounting drive, please wait", after which point it should be available on the Places menu.  Good luck!

---

### Post by MadMedis on 2008-03-22
Sorry, I didn't read the second page of the thread.  LOL

Glad you got it working!

---

