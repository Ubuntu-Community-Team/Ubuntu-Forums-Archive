---
title: "Xp over Ubuntu"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Da King on 2007-12-13
I installed Gusty bt now i think some of the programs i wod use to work will only work in windows my question is is it possible to install XP without spoiling my ubuntu so i dual boot? if possible how do i go about it.

---

### Post by skymera on 2007-12-13
if you install XP now you will overwrite you Grub.

so when install is done boot Live CD and reinstall Grub, done.

also have you considered Wine?

sudo apt-get install wine

---

### Post by chubbers on 2007-12-13
Use Wine Windows emulator, go to add and remove and search for WINE at the top, this will search through all the diffrent sites and get you the download, but change in the top right, to all supported programs, the select all the programs, 

Many thanks , Chubbers :)

---

### Post by mcduck on 2007-12-13
Yes, it's possible but it requires a bit of work.

First, Windows install isn't able to resize partitions to make more space for you, so if you don't have free disk partition (or another hard disk) for Windows you need to make one before hands, for example with Ubuntu's live-CD and Gparted. Also as Windows sees Linux file systems as empty, unformatted partitions, you'll need to be very careful when selecting where to install Windows to avoid overwriting your Ubuntu install.

Second, Windows doesn't like any other operating systems, so it will overwrite your boot loader (Grub) with it's own, making it impossible to boot into Ubuntu. You'll need to reinstall Grub after you have installed Windows. This can also be done with Ubuntu's live-CD.

Here's a guide to reinstalling Grub: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by innuendosoft on 2007-12-13
If you are thinking of using XP from inside Ubuntu, another option you have is virtualization. This means you'll be running XP (or any other operating system you need) as if it was a program. I'd suggest using QEMU for vitualization, although there are alternatives.
As chubbers states, you can also use WINE, however, I have to say there are quite a lot of apps that won´t work with it due to program dependencies.

Regards ad best of lucks.

---

### Post by philinux on 2007-12-13
> **Da King said:**
> I installed Gusty bt now i think some of the programs i wod use to work will only work in windows my question is is it possible to install XP without spoiling my ubuntu so i dual boot? if possible how do i go about it.

Wine is to say the least, unpredictable. But which programs do you need.

There may be a linux equivalent thats just as good.

---

### Post by subs on 2007-12-13
try running a virtual windows machine in ur ubuntu..... it will be easier that trying to reinstall grub....

---

### Post by eldepeche on 2007-12-13
> **chubbers said:**
> Use Wine Windows emulator

Wine Is Not an Emulator!

---

### Post by Da King on 2007-12-13
Well i have over all this things before i decided to install windows, my ubuntu doesnt see my bluetooth dungle even thouh windows see's it, secondly, i cant copy CD - CD when it is a VCD, i cant burn from mp3 to audio meanwhile i was told K3B was the best burning program yet all this failed. i also work with a lot of cell phones like SE,samsung,nokia,etc...most of this phones only have windows installation and last of all ubuntu doesnt see my vga card is a 3D card so i cant paly so many games. 

is there another way of burning my whole ubuntu os onto a dvd?

thank all of u for ur advice too.

---

### Post by subs on 2007-12-13
to get most of *samsung, nokia phones *working in ubuntu try kmobile tools.... its meant for KDE but works as well in GNOME.....

the vga card problem is kind of related to compiz and ubuntu7.10 .... the window composting software in ubuntu gutsy does not have supported drivers for almost all intel integrated graphics cards.....

---

### Post by Het Irv on 2007-12-13
> **Da King said:**
> Well i have over all this things before i decided to install windows, my ubuntu doesnt see my bluetooth dungle even thouh windows see's it, secondly, i cant copy CD - CD when it is a VCD, i cant burn from mp3 to audio meanwhile i was told K3B was the best burning program yet all this failed. i also work with a lot of cell phones like SE,samsung,nokia,etc...most of this phones only have windows installation and last of all ubuntu doesnt see my vga card is a 3D card so i cant paly so many games. 

is there another way of burning my whole ubuntu os onto a dvd?

thank all of u for ur advice too.
Don't forget to install the restriced extras package for the codex for mp3 and other formats.
(I forgot the line of code can someone post it please)

---

### Post by subs on 2007-12-13
> **Het Irv said:**
> Don't forget to install the restriced extras package for the codex for mp3 and other formats.
(I forgot the line of code can someone post it please)



this should do it....

> sudo apt-get install ubuntu-restricted-extras

---

### Post by Da King on 2007-12-14
this was what i got


```


sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

i already had it and i still cant burn to audio, what about my bluetooth dongle? ubuntu doesnt see anything connected.

---

### Post by seshomaru samma on 2007-12-14
for blue tooth try this:
[http://ubuntuforums.org/showthread.php?t=586105](http://ubuntuforums.org/showthread.php?t=586105)
[http://blueman.tuxfamily.org/](http://blueman.tuxfamily.org/)
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

for burning , 
k3b should work , what kind of errors are you getting?

---

### Post by subs on 2007-12-15
> **Da King said:**
> this was what i got


```


sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```i already had it and i still cant burn to audio, what about my bluetooth dongle? ubuntu doesnt see anything connected.



:lolflag::lolflag:

the restricted extras where for the proprietary codecs for videos and music files and not for any hard ware:guitar:

---

### Post by mcduck on 2007-12-15
> **Da King said:**
> this was what i got


```


sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

i already had it and i still cant burn to audio, what about my bluetooth dongle? ubuntu doesnt see anything connected.

I believe K3B uses Xine's codecs for this, so you need to install them. They are not part of the restricted extras-package. Or try some other burning application instead, both Gnomebaker and Brasero are excellent burners and as a bonus they are also native Gnome applications..

---

### Post by Riffer on 2007-12-15
I had the same problem burning a mp3 cd when I first got onto Ubuntu.  Its seems, at least in my case is that you burn them as a data disk.  Hope this helps.

---

