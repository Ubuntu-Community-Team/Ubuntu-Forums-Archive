---
title: "How do I install Windows XP over Ubuntu?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-01-09
After installing Ubuntu Edgy Eft, I accidentally deleted my partitions and all my old files including windows XP. I don't like to do this but I'm left with no choice. I have to install Windows XP in order for me to print scan since I still cannot find a driver for my Canon PIXMA MP150. 

How do I make my laptop dual boot with XP and Ubuntu. 

Don't worry. After finding the drivers, I'll delete my Windows again. ;)

Edit:
I forgot to mention that my Scanner is not my only problem. Actually, I can't make my usb mouse work, I can't sync my music files with my Sony Network Walkman, and I can't use my webcam. Lots of problems but hopefully, I solve them in about a month

---

### Post by rbhigday on 2007-01-09
I think i remember reading somewhere here for dual boot you must install the xp first then install ubuntu.

Ubuntu will install a grub menu giving you the options to boot to another os. Ubuntu will be the default boot os unless you change it

---

### Post by teaker1s on 2007-01-09
install xp to free partition and reinstall grub

---

### Post by wersdaluv on 2007-01-09
Does that mean I have to reformat again?

---

### Post by wersdaluv on 2007-01-09
> **teaker1s said:**
> install xp to free partition and reinstall grub

So I dont have to make some special installation stuff? Will my Ubuntu OS be preserved?

---

### Post by Ben Sprinkle on 2007-01-09
Install Windows over ubuntu, in a seperate partition. Then reinstall Ubuntu over the other Ubuntu partition. It will auto detect it and add an entry, alternative is:
```

sudo gedit /boot/grub/menu.lst

```
Scroll down to the list and add an entry like this:
```

title Microsoft Windows XP
root (hd0,1)
savedefault
makeactive
chainloader +1

```
The root(0,1) means hard drive 0, partition 1, where Windows XP is located.

---

### Post by whee on 2007-01-09
If you don't have a driver for your scanner you can use VueScan.(Runs on WinXP, Linux and OSX)
VueScan is an application that supports many scanners and gives you even more options and often scans with better quality than native drivers.
For some reason the drivers for my Canon scanner don't work anymore on Windows XP Pro, so ever since i use VueScan, which enables me to still use my scanner...and it does so excellently.

---

### Post by wersdaluv on 2007-01-09
> **Goat Spirit said:**
> Install Windows over ubuntu, in a seperate partition. Then reinstall Ubuntu over the other Ubuntu partition. It will auto detect it and add an entry, alternative is:
```

sudo gedit /boot/grub/menu.lst

```
Scroll down to the list and add an entry like this:
```

title Microsoft Windows XP
root (hd0,1)
savedefault
makeactive
chainloader +1

```
The root(0,1) means hard drive 0, partition 1, where Windows XP is located.

Since you said I have to reinstall Ubuntu, I assume that the installation of XP will delete Ubuntu. Will it delete all my other files in my Ubuntu partition? (Music, OOo Documents, etc.)

---

### Post by wersdaluv on 2007-01-09
I think I got what you mean! What you mean was reinstall GRUB instead of Ubuntu. Is that what you mean? I just want to be sure.

---

### Post by Ben Sprinkle on 2007-01-09
> **wersdaluv said:**
> Since you said I have to reinstall Ubuntu, I assume that the installation of XP will delete Ubuntu. Will it delete all my other files in my Ubuntu partition? (Music, OOo Documents, etc.)

Only if you wnat to, I mean just reinstall your stuff but keep your files backed up on another partition or something.

---

### Post by wersdaluv on 2007-01-14
I have successfully installed XP on a partition while my Ubuntu is untouched in the other (I presume). 

Now, whenever I boot my laptop, it automatically runs XP. 

How do I get my laptop run GRUB in the begginning for me to choose which OS to use?

---

### Post by bulldog on 2007-01-14
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
This will get you a grub> prompt 
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by kinematic on 2007-01-14
> **Goat Spirit said:**
> Install Windows over ubuntu, in a seperate partition. Then reinstall Ubuntu over the other Ubuntu partition. It will auto detect it and add an entry, 

please don't give advice like that again....don't install an OS over another OS....always format before installing an OS.

---

### Post by Ben Sprinkle on 2007-01-14
> **kinematic said:**
> please don't give advice like that again....don't install an OS over another OS....always format before installing an OS.

You do not know what you are talking about. You do not need to format first. I never do.
You can just install over anoter if you want, makes no difference.

---

### Post by wersdaluv on 2007-01-14
> **bulldog said:**
> Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
This will get you a grub> prompt 
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

Thank you very much! I will try that. :)

---

### Post by Ben Sprinkle on 2007-01-15
No problem. Glad to see someone appreciates advice.

---

### Post by wersdaluv on 2007-01-15
> **bulldog said:**
> Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
This will get you a grub> prompt 
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

After doing the steps above, GRUB was already installed but I don't see Windows in the OS choices. What can I do?

---

### Post by wersdaluv on 2007-01-15
> **Goat Spirit said:**
> No problem. Glad to see someone appreciates advice.

:) I always have to thank you guys. You are just volunteers but you help me so much. :)

---

### Post by CroEragon on 2007-01-15
I think you do not have to reinstall Ubuntu. Just install XP on partition when it was before and then use one of ways to reinstall grub. I would recommend using SuperGRUB. You do not have to reinstall Ubuntu.

---

### Post by Sef on 2007-01-15
> After installing Ubuntu Edgy Eft, I accidentally deleted my partitions and all my old files including windows XP. I don't like to do this but I'm left with no choice. I have to install Windows XP in order for me to print scan since I still cannot find a driver for my Canon PIXMA MP150.


Check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").  

From the TestDisk website: > TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting your Partition Table). Partition table recovery using TestDisk is really easy.

---

### Post by sailor2001 on 2007-01-15
I use MEPIS to repair or restore grub. That's a light weight OS and easy to use......just click on install center and look for the "repair grub"

---

### Post by ljpm on 2007-01-15
> **wersdaluv said:**
> After doing the steps above, GRUB was already installed but I don't see Windows in the OS choices. What can I do?

As Goat Spirit stated earlier...


You need to add 
```

title Microsoft Windows XP
root (hd0,1)
savedefault
makeactive
chainloader +1

```

to /boot/grub/menu.lst

to do this enter and copy and past the above at the end of the file.

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Ben Sprinkle on 2007-01-15
You might have update your devices list:
```

sudo gedit /boot/grub/device.map

```
Mine looks like this:
```

(hd0)	/dev/hda
(hd1)	/dev/sda

```
I have 2 hard drives. My hd0 is where Linux and Windows are on.
My hd1 is my external 120gb storage hard drive. ;)

---

### Post by wersdaluv on 2007-01-16
Thanks! Worked like magic! :)

---

### Post by birdseye on 2007-01-16
I had the USB mouse problem and it was as simple to solve as enabling the usb mouse in boot. I guess XP detects the mouse and boots up a driver even when the uSB mouse is disabled in boot.Certainly with it disabled in boot I still had a working mouse, and a problem with XP detecting a mouse every time I connected up a Garmin GPS - but thats a different frustrating story,](*,) 

If you find an answer to the canon printer prob, let me know - I'm still struggling, and its the last major prob I have with Ubuntu

---

### Post by wersdaluv on 2007-01-16
> **birdseye said:**
> I had the USB mouse problem and it was as simple to solve as enabling the usb mouse in boot. I guess XP detects the mouse and boots up a driver even when the uSB mouse is disabled in boot.Certainly with it disabled in boot I still had a working mouse, and a problem with XP detecting a mouse every time I connected up a Garmin GPS - but thats a different frustrating story,](*,) 

If you find an answer to the canon printer prob, let me know - I'm still struggling, and its the last major prob I have with Ubuntu

How did you fix the mouse problem? In my case, whenever I have my USB mouse connected since the booting up of my laptop, it works but the mouse pointer responds very slowly. 

What canon printer do you have?

---

