---
title: "Help"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by spanerman on 2007-05-12
ive just installed ubuntu and i rebooted to check if i still had windows and its gone!!! i cant chose to boot windows!! help

---

### Post by liamwithers on 2007-05-12
So you didn't partion with space for Windows and Linux?

Silly :P

---

### Post by spanerman on 2007-05-12
i was told you didn't need to!! i thought the installer did it... im sure it asked me about it!

---

### Post by heimo on 2007-05-12
On terminal, run (and show us the output)
```
sudo fdisk -l 

```

---

### Post by starcraft.man on 2007-05-12
> **spanerman said:**
> i was told you didn't need to!! i thought the installer did it... im sure it asked me about it!

Ummmm, did you tell it to simply partition the whole hard drive? If so... ummmm, windows is gone bye bye. >.>

Do run Heimo's command, terminal is Applications > Accessories > Terminal.

---

### Post by jfinkels on 2007-05-12
> **spanerman said:**
> i was told you didn't need to!! i thought the installer did it... im sure it asked me about it!

What is the output of this command (type this in the terminal and tell us what it says):
```
sudo fdisk -l
```

---

### Post by alienexplorers on 2007-05-12
If you told it to use free space it would not delete windows.  Otherwise bye-bye windows.

---

### Post by alinuxfan on 2007-05-12
> **spanerman said:**
> ive just installed ubuntu and i rebooted to check if i still had windows and its gone!!! i cant chose to boot windows!! help


at the partition manager, did you choose the option "erase entire disk"?

If you did, I hope you had your files backed up, and that you don't need Windows anymore.

I paid the M$ tax on my lappy so i still have a Windows partition, but miraculously, it keeps getting smaller...i think 12Gig right now :p

---

### Post by spanerman on 2007-05-12
im sure i told it to take free space!!!


steven@steven-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7204    57866098+  83  Linux
/dev/hda2            7205        7297      747022+   5  Extended
/dev/hda5            7205        7297      746991   82  Linux swap / Solaris
steven@steven-desktop:~$ 


was the result from that command

---

### Post by heimo on 2007-05-12
Sorry to say, but there's no Windows partition there. :(

---

### Post by spanerman on 2007-05-12
so what to do? i have the windows repair disc will that do anything?

---

### Post by Campingman on 2007-05-12
Yes I know people should read carefully and take care, but there really needs to be a BIG warning box telling them this option is going to erase the whole hard drive before continuing.  This post topic seems to be getting quite common just lately!

---

### Post by LE CHARBON on 2007-05-12
Reinstall and reformat:popcorn:

---

### Post by Campingman on 2007-05-12
> **spanerman said:**
> so what to do? i have the windows repair disc will that do anything?

Reinstall windows, you may have to reformat to NTFS first, then install Ubuntu again, it is probably the easiest option.

---

### Post by starcraft.man on 2007-05-12
> **spanerman said:**
> so what to do? i have the windows repair disc will that do anything?

You'll have to reinstall windows first, then give Ubuntu another try and I suggest you read these [two]("http://www.psychocats.net/ubuntu/installing") [pages.]("http://www.psychocats.net/ubuntu/partitioning")

Please be sure you don't delete any partitions, maybe even doing the partitions manually its not too difficult.

---

### Post by LE CHARBON on 2007-05-12
POOKZ on another thread did the same thing. :(

---

### Post by spanerman on 2007-05-12
im just reinstaling windows now (im on a diff pc) once im done and i want to install ubuntu what should i do differently??

---

### Post by starcraft.man on 2007-05-12
> **spanerman said:**
> im just reinstaling windows now (im on a diff pc) once im done and i want to install ubuntu what should i do differently??

Read my two links higher up, and make the partitions manually, they are explained in the links :)

That should be all, best of luck. I try to get people to stay away from the automatic installer, its impossible to delete your windows partition manually unless you choose to :)

---

### Post by spanerman on 2007-05-12
ok im trying to use the ubuntu partitioner as in that tuorial but i only have the use all disk space and manual options.....what should i do???

---

### Post by spanerman on 2007-05-12
anyone want to tell me how to partition manualy................all i have is the base files for xp.....

---

### Post by Campingman on 2007-05-12
> **spanerman said:**
> anyone want to tell me how to partition manualy................all i have is the base files for xp.....

All I can do is point you to a guide of what partitions to use, the manual partition process is quite easy to use when you get into it, just remember root needs to be defined as / (will become clear when you are doing it)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

If still not clear, i am sure someone can come up with a clearer instruction for you

---

### Post by spanerman on 2007-05-12
thats usefull but it doesnt actualy tell me what to do to create different partitions all i need is a 50-50 split......please help

---

### Post by LE CHARBON on 2007-05-12
SHOULD LOOK SOMETHING LIKE THIS.

Partition List:
- XP Partition, NTFS, X GB, mount /media/hdsomething (can change)

- Ubuntu Partition, Ext3, 6-8 GB, mount /

- Swap File, Swap, 2-3 GB, doesn't mount like drives

- Home partition, Ext3, rest of your drive GB, mount /home

The / is your root directory and you mount your home seperate so that you can keep your data if you reformat your version of Ubuntu.

After your done setting it up, grub will detect your XP install unless its corrupted

---

### Post by Campingman on 2007-05-12
> **spanerman said:**
> thats usefull but it doesnt actualy tell me what to do to create different partitions all i need is a 50-50 split......please help
 If you select manual edit when in the install process it opens up Gparted which is a partitioning tool, you can then do the necessary from there.

---

### Post by st33med on 2007-05-12
Alright, lemme help. Click Manual Partition and click next. Now, you should see a graph with Windows partition, namely ntfs. Right-click on the NTFS and decrease the amount of space it has in half. Now, there should be an option somewhere to add a partition and add an ext3 partition with the amount you decreased, but decrease the number by 1GB(or 1024 MB). Now add an extended partition with the full 1 GB. Below it, add a logical partition named linux-swap with 1 GB. Continue with the setup, and you should be fine!

---

### Post by Campingman on 2007-05-12
This has some screen shots of Gparted in the install process and explains how to use it
[http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)
This is for edgy I think but the principle is the same

---

### Post by spanerman on 2007-05-12
ive done it manualy but when i click next it asks me to specify the root system....how do i do this?


and i cant make the /media/hd6 partition a ntfs??? what to do?

---

### Post by Campingman on 2007-05-12
> **spanerman said:**
> ive dont it manualy but when i click next it asks me to specify the oot system....how do i do this?
Root is / I cannot remember the  the exact process but I think if you go into edit on the partition menu there is a pull down menu where you can select the type ie swap, / .  You need to select / as root  
It does cover it here in mount points 
[http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)

Why NTFS, why not fat?

---

### Post by Happy_Man on 2007-05-12
Right, when you get to that screen, right-click on the partition you want Ubuntu to use and replace /media/sd<whatever number it is> with just plain old / . That should do it!

Somebody really needs to fix that in Ubiquity, the number of posts on that issue grows every day.

---

### Post by spanerman on 2007-05-12
well i hope ive done it correctly!!! wel soon find out...........

---

### Post by Campingman on 2007-05-12
Fingers crossed !!!!

---

### Post by spanerman on 2007-05-12
it didnt work!!!!!!11 oh well who needs windows on more than 1 pc anyway? i will try doublebooting when i learn more about it. for now im goin to get used ti ubuntu!

---

### Post by spanerman on 2007-05-13
another question guys.....the too things i lover are youtube and msn.....i can use the ubuntu msn program but its lacking...and i cant install flash to use youtube....what can i do to stop this...

---

### Post by jfinkels on 2007-05-13
> **spanerman said:**
> another question guys.....the too things i lover are youtube and msn.....i can use the ubuntu msn program but its lacking...and i cant install flash to use youtube....what can i do to stop this...

Do you mean aMSN or Gaim? If you don't like one, you can try the other!

Try downloading the 'flashplugin-nonfree' package. First, enable the 'multiverse' repository in 'System > Administration > Software Sources'. Then, type the following in the terminal:
```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

---

