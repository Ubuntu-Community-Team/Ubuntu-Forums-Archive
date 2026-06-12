---
title: "BIOS and windows do not recognize external hard drive"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Nate7679 on 2007-03-03
After running into alot of trouble installing 6.1 on my external hard drive, I gave it to a friend who installed 5.1 on it. He was able to boot from it by putting it in his desktop computer. I havent been able to boot from it on my laptop computer as an external drive because windows doesnt recognize it and neither does the BIOS. there is no option for any removable media or USB device in the BIOS, and im wondering what I should change. the laptop is a sony vaio and the hard drive is a 40gb western digital.

---

### Post by carlosfocker on 2007-03-03
under boot option in the bios there is no boot from usb device.  If not you might want to check bois updates for that model

---

### Post by omrsafetyo on 2007-03-03
> **carlosfocker said:**
> under boot option in the bios there is no boot from usb device.  If not you might want to check bois updates for that model

Some versions of BIOS also don't have specifically "USB" - it may be "removable storage" or "other devices" or something to that effect.  I would check for each of these options - and if either is there, use that is your first boot device.

---

### Post by PaulFXH on 2007-03-03
If your BIOS does not recognise a USB HDD as bootable, you can try [this option]("https://help.ubuntu.com/community/BootFromUSB").
I have used this to boot to a number of Linux flavours stored on an external USB drive and it works very well.
Good luck.

---

### Post by Nate7679 on 2007-03-03
There is no mention of anything related to removable storage. Im updating my system BIOS, and im gonna try it again.

and honestly, I'd rather wait for an alternative to booting from a disc in addition to a drive, but if thats what i need to do i can do it.

Also, could this have anything to do with the jumpers on the hard drive?

---

### Post by omrsafetyo on 2007-03-03
> **Nate7679 said:**
> There is no mention of anything related to removable storage. Im updating my system BIOS, and im gonna try it again.

and honestly, I'd rather wait for an alternative to booting from a disc in addition to a drive, but if thats what i need to do i can do it.

Also, could this have anything to do with the jumpers on the hard drive?

The jumpers won't matter in this case. They determine the primary/secondary functions - and only relate to which channel they are attached to on the MOBO... for isntance the primary IDE channel.  Since you are using USB, the jumper should be more or less ignored.. it could be primary, slave, or cable select - it shouldn't matter.

---

### Post by Nate7679 on 2007-03-03
I installed the BIOS update provided by sony and it didnt detect any removable storage devices, including an external hard drive that was also connected with USB.

So I booted 6.1 from the installer disc, and it was unable to find anything on the external hard drive that has 5.1 installed on it, but said that it was completely full. The disc was also named "dell utility", if that makes any difference. Could it be possible that my computer does not support booting from usb?

---

### Post by confused57 on 2007-03-03
> **Nate7679 said:**
> I installed the BIOS update provided by sony and it didnt detect any removable storage devices, including an external hard drive that was also connected with USB.

So I booted 6.1 from the installer disc, and it was unable to find anything on the external hard drive that has 5.1 installed on it, but said that it was completely full. The disc was also named "dell utility", if that makes any difference. Could it be possible that my computer does not support booting from usb?

With the USB drive plugged in and with the live cd booted, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"
This command will show your partitions on your drives, hopefully on your external drive also.

Windows may recognize your external drive(formatted with ext3?) with this driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Just out of curiosity, while you're booted into the live cd, open a terminal, enter:
```
sudo grub
find /boot/grub/stage1
```

```
quit
```
to exit the grub prompt

---

### Post by PaulFXH on 2007-03-03
> There is no mention of anything related to removable storage
The article is about booting from usb drives which are removable storage devices.
In any event, whether or not you are convinced by the article, I can say that I was and used it very successfully to boot to both Mepis and PCLinuxOS from an external HD.
I know it looks a little forbidding, but it's actually quite easy.
But, it's up to you if you have a more convenient means to achieve your objective,

---

### Post by Nate7679 on 2007-03-04
I'll try the guide, but there are still alot of things in it that I dont really understand so if I do ill probably post questions I have here.

The other thing I tried is the install.exe/Prototype which can be found here:

[https://wiki.ubuntu.com/install.exe/Prototype](https://wiki.ubuntu.com/install.exe/Prototype)

Which is exactly what i'm looking for, but it dosent save any of the changes I make to the system and its still really buggy.

The reason I want to install it and boot it from an external hard drive is because I'm want to be able to plug it in and use ubuntu, but then unplug it and have it boot up windows XP completely normal. Also because I dont want to have to deal with partitioning my hard drive and re-installing windows.

---

### Post by PaulFXH on 2007-03-04
> because I dont want to have to deal with partitioning my hard drive and re-installing windows.

You DON'T have to re-install Windows to set up a dual boot system but you DO have to set up additional partitions.
But this really is a piece of cake as long as you have the space on your internal HD.
The time required to set up a dual boot system would be about two hours and this includes partitioning the HD and updating the installed Ubuntu OS. For all but about 10 minutes of these two hours the user is actually doing nothing other than watching the changes on the screen.
So, it really is no big deal.
Nevertheless, there always is the danger that problems may occur and therefore preparation in essential. Read up on the various guides and ask questions in the forums before you start.

---

### Post by Nate7679 on 2007-03-05
One other thing, when I boot from the DVD and my external is plugged in and turned on it says 

"sda: assuming drive cache: write through"

When i entered in sudo fdisk -l 

i got alot about my internal hard drive, which i didnt think would be useful. but i also got something similar about my external:


Disk /dev/hda: 39.9 GB, 39999999488 bytes
255 heads, 63 sectors/track, 4823 cylinders
Units: cylinders of 16065 * 512 = 8225280 bytes

Device      Boot     Start     End        Blocks       Id      System

/dev/sda1     *           1     4770    38314993+   83     Linux
/dev/sda2             4771    4863        747022+    5      Extended
/dev/sda5             4771    4863        746991     82      Linux swap / Solaris


When i typed in find /boot/grub/stage1 i got

  (hd1,0)

I hope this helps.

---

### Post by confused57 on 2007-03-06
> **Nate7679 said:**
> One other thing, when I boot from the DVD and my external is plugged in and turned on it says 

"sda: assuming drive cache: write through"

When i entered in sudo fdisk -l 

i got alot about my internal hard drive, which i didnt think would be useful. but i also got something similar about my external:


Disk /dev/hda: 39.9 GB, 39999999488 bytes
255 heads, 63 sectors/track, 4823 cylinders
Units: cylinders of 16065 * 512 = 8225280 bytes

Device      Boot     Start     End        Blocks       Id      System

/dev/sda1     *           1     4770    38314993+   83     Linux
/dev/sda2             4771    4863        747022+    5      Extended
/dev/sda5             4771    4863        746991     82      Linux swap / Solaris


When i typed in find /boot/grub/stage1 i got

  (hd1,0)

I hope this helps.

Unless your bios can boot first to the external drive, you probably won't be able to set your system to boot into the external drive first, without some 3rd party software.

I have an idea, which may or may not work, is maybe trying the GAG bootloader:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)
you can make a GAG boot floppy or cd

GAG would hopefully be able to boot your external drive, if grub is installed to the root partition of the drive.
I think I gave you the link earlier for installing grub with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Using the directions in this link, you would:
```
sudo grub
find /boot/grub/stage1
root (hd1,0)
setup (hd1,0)
quit
```

You would need the GAG floppy or cd to boot your external drive, but you would still be able to boot your Windows internal drive if the external hd is disconnected...just an idea.

---

### Post by Nate7679 on 2007-03-06
> **PaulFXH said:**
> You DON'T have to re-install Windows to set up a dual boot system but you DO have to set up additional partitions.
But this really is a piece of cake as long as you have the space on your internal HD.
The time required to set up a dual boot system would be about two hours and this includes partitioning the HD and updating the installed Ubuntu OS. For all but about 10 minutes of these two hours the user is actually doing nothing other than watching the changes on the screen.
So, it really is no big deal.
Nevertheless, there always is the danger that problems may occur and therefore preparation in essential. Read up on the various guides and ask questions in the forums before you start.

My internal HD is about 80gb, but i have 500gb of space in external drives, so i dont use my internal much. Would this be enough to run Windows XP and ubuntu? Also, if i was to ever upgrade to Vista (not likely), how difficult would that be?

As for partitioning, I'm under the impression that you must erase your hard drive before you can partition it. So how could I partition my drive that has windows on it without erasing it?

---

### Post by PaulFXH on 2007-03-07
> My internal HD is about 80gb, but i have 500gb of space in external drives, so i dont use my internal much. Would this be enough to run Windows XP and ubuntu?
Coincidentally, one of my computers has an 80GB internal HD which has not only WinXP and Ubuntu installed , but Zenwalk and Debian as well. So, yes, you have enough room.

> Also, if i was to ever upgrade to Vista (not likely), how difficult would that be?
Given that you have the external HD, 25GB is absolutely oodles of space for Ubuntu. That leaves about 55GB for Vista. Although I have no experience with Vista, I really cannot imagine it's going to need even half of this.

> As for partitioning, I'm under the impression that you must erase your hard drive before you can partition it
Your impression is totally incorrect. You DO NOT have to wipe your HD to partition it.

> so how could I partition my drive that has windows on it without erasing it?
Use Gparted which is a marvellous partitioning tool (as well as being free). This will allow you to do anything you want: add partitions, take out partitions, resize partitions all without deleting any stuff you already have on your HD.
Of course, you can never be totally certain that thing won't go wrong, so back up everything that's important before you start just in case.
Nevertheless, I've done a lot of partitioning and I've never had a problem.

Just for your information, I have three partitions for Ubuntu: Swap 1.5GB, Root 8GB and Home 15GB. The Home partition is kinda like My Documents in Windows and it is very useful if you need to re-install Ubuntu. Then, as long as you don't re-partition the Home partition, you can avoid having to reconfigure your computer to have it just like it was before.

---

### Post by Nate7679 on 2007-03-07
Well that changes almost everything. Booting off of an external hard drive would be such an inconvenience on a laptop, especially if i had to boot from a disc and do other things just to accomplish it. 

So ill definitely looking into partitioning my hard drive. How will booting up work though, will it just be selecting an operating system or will i have to enter in a command?

---

### Post by PaulFXH on 2007-03-08
Well, you're sure not rushing into this without investigating every aspect of the operation.
While this is indeed commendable, it is not necessary to exaggerate this.
When you set up a dual-noot system, you will get a boot menu when you boot up. This will contain your two OSes together with the Recovery mode option for Ubuntu. Additionally it will have a MemTest option.
When you see this, it is just a matter of using the up/down arrow keys to select whichever OS you want. No commands are necessary or indeed possible.
You can also rearrange this boot menu including adding splashimages if your aesthetic tastes don't allow you to be satisfied with the rather drab boot menu you get from Grub (bootloader).

---

### Post by PaulFXH on 2007-03-08
Well, you're sure not rushing into this without investigating every aspect of the operation.
While this is indeed commendable, it is not necessary to exaggerate it.
When you set up a dual-noot system, you will get a boot menu when you boot up. This will contain your two OSes together with the Recovery mode option for Ubuntu. Additionally it will have a MemTest option.
When you see this, it is just a matter of using the up/down arrow keys to select whichever OS you want. No commands are necessary or indeed possible.
You can also rearrange this boot menu including adding splashimages if your aesthetic tastes don't allow you to be satisfied with the rather drab boot menu you get from Grub (bootloader).

---

### Post by Nate7679 on 2007-03-10
> **PaulFXH said:**
> Well, you're sure not rushing into this without investigating every aspect of the operation.

Point taken, but i really don't want to erase my hard drive/blow up my laptop trying to install ubuntu.

I think im gonna do it though, is there any guide that I can follow to installing it on a partitioned hard drive?

---

### Post by PaulFXH on 2007-03-11
You could try this [guide here]("http://www.psychocats.net/ubuntu/installing") but there are very many howtos available.
Note that many earlier guides say that you DO NOT want to let Grub (bootloader) replace your Windows MBR (master boot record). However, there is absolutely no problem with this these days and indeed it is to be recommended. So, say "yes" when it comes to this choice in the installation.
I have never used the partitioner during the installation and prefer to use Gparted (burn to a live CD) to do the partitioning before-hand. Therefore, I would always go the Manual partitioning route at the partitioning step.
Good luck

---

### Post by Nate7679 on 2007-03-11
Alright, im almost ready to go, im just not sure how exactly to partition my hard drive. I want it set up as this picture below, so that I have a partition for my windows operating system, a partition for the ubuntu operating system, a partition for the swap, a home partition, and also a partition for my personal files so that they can be accessed by both ubuntu and windows xp, as shown in this picture. 

[http://www.psychocats.net/ubuntu/images/partitioning4.png](http://www.psychocats.net/ubuntu/images/partitioning4.png)

That image is basically how i would like my hard drive set up.

This is a screenshot I took of gparted from the installer. 

[http://i132.photobucket.com/albums/q3/Nate7679/Screenshot.png?t=1173651724](http://i132.photobucket.com/albums/q3/Nate7679/Screenshot.png?t=1173651724)

What is the smaller, 6gb partition for? Is that just the windows operating system files partition?

Should I create one 25gb partition out of the empty space of the 68.52 partition, and leave the part with files on it alone or do i need to change it to fat32 first? would that do anything to my files?

And how should I partition that 25gb of empty space? Am i correct in assuming that it will bring up a screen like this for me to set up the mount points?

[http://img130.imageshack.us/img130/5541/w2u31b7pl.png](http://img130.imageshack.us/img130/5541/w2u31b7pl.png)

If so, how should i set up the mount points? Again, I know I need 1.5gb for swap, 8 for root and i think a 15.5 section for home.

I'm sorry im asking so many questions, but I really dont want to make a mistake that would erase any important files. even though ive made a backup, it would be a pain to reinstall windows and restore it.

---

### Post by Nate7679 on 2007-03-11
Okay, so i figured out alot of the problems i was having and I came up with this:

[http://i132.photobucket.com/albums/q3/Nate7679/Screenshot2.png?t=1173660975](http://i132.photobucket.com/albums/q3/Nate7679/Screenshot2.png?t=1173660975)

I have a 20gb extended partition from which i have three logical partitions: 2gb for swap, 8gb for root files where i will install too, and 10gb for my home folder. I decided that I would figure out how to make my windows files common at a later time.

So my question is, can i move ahead with the partitioning or is there any changes i should make?

---

### Post by Nate7679 on 2007-03-12
Well, I think i managed to install it. Windows is still installed, ubuntu is installed, and they both seem to boot with no problems. If i have any, ill make another post here.

I appreciate everyones help alot. Thank you all very much.

---

### Post by PaulFXH on 2007-03-12
Glad it worked out.
A lot easier than you thought, right?

---

