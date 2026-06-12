---
title: "Cannot Resize Partition"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by jmusso on 2007-06-26
Okay, I used the search function and wasn't coming up with anything that fit my problem...

I'm pretty much a complete noob when it comes to computers, I mean I understand how some basic stuff works, but not much past that. So bear with the noobishness here please. And I hope no one already posted on this, I couldn't find it anywhere...

I'm running a Compaq Presario V5000 with an AMD Sempron chip, a Radeon XPress 200m, XP Home Edition, and an 80gb HD. I've downloaded and burned to CDs both the Ubuntu (newest version 7.somethingorother) liveCD (thats the default download right?) as well as the Alternative install disc. In both scenarios it seems I'm running in to the same problem:

I cannot resize my partition. The default option in the partitioning menu for Ubuntu is to put it on the whole disc. I don't want to do that. I intend to run a dual-boot with my XP so I can access XP normally and more or less "try out" Ubuntu on the hard drive. When I attempt to manual partition it (I don't really know what I'm doing there) I can't change the size of the main NSTF partition, which is the partition I believe I want to use. There's also a smaller FAT32 partition, but I think that's the recovery partition... anyways, I DO NOT get the slider option ever. I've never seen the slider, only in screenshots, and I don't understand why I can't just let Ubuntu manually resize my partition... Please offer some advice.

---

### Post by bodhi.zazen on 2007-06-26
Defragment the partition first, twice is typically sufficient.

---

### Post by jmusso on 2007-06-26
I defragged twice, had a bunch of files that wouldn't defrag, I'm not sure if that's normal or not... Anyways, I did a Disk Cleanup inbetween defrags to see if it would help. End result: same problem as before. Ubuntu, or whatever partitioning program, won't resize the partition. Suggestions please?

---

### Post by ramjet_1953 on 2007-06-26
Are you booting your system using the live CD, or a stand-alone PartEd disk?

You cannot re-size a disk that is mounted.

Regards,
Roger :cool:

---

### Post by jmusso on 2007-06-26
I tried both the LiveCD and the alternative disk, using the text install. I'm not sure what a PartEd disk is.

How do I tell if my disk is mounted? If so, how do I unmount it? I just want to install Ubuntu and still be able to use Windows XP for the time being...

---

### Post by jmusso on 2007-06-26
Also: I just tried it again from the alternative disk using the text installer. When I tried the first partition option, the Guided one where it resizes hda1 or whatever, it said that it could not resize this partition for an unknown reason, and that i should check virtual console 4 or something... it also gave me a command line to enter but i forget what it was. Does this help any...?

---

### Post by jmusso on 2007-06-27
Here's my update of the situation. 

I downloaded and booted up the GParted LiveCD. When I did this, I selected the first option, the gparted automatic whatever. Once GNOME powered up, I tried to select the NTSF partition, which is the one I want to shrink and make room for a Ubuntu partition. However, a small warning icon is displayed next to it. When I double-click on the partition, a message comes up telling me to run chkdsk, then reboot twice (in Windows). I did so, and tried it again. Same exact message and icon. It says it will not be able to alter this partition until it is repaired. Any idea what I'm dealing with?

Someone please help. I WANT Ubuntu!!!!

---

### Post by jrev on 2007-06-27
Hi,
Is your windows system operating OK ?

How large is your hard disk ? 

How much space is using your windows system ?

You can see all that on the gparted windows ...

---

### Post by jmusso on 2007-06-27
Thanks. How can I see all this though...?

---

