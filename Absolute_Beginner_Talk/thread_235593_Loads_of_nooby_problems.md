---
title: "Loads of nooby problems"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Joe of loath on 2006-08-13
ok most important first. i need drivers for my belkin wireless card. do they exist? it is a ummm F5D7000? that seems right.second most important is i cannot play music files in rythmbox. they are all mp3, and i have set the cdrom drive (where all my music is stored :$) and urr it doesnt do anything. totem doesnt work either. and finally i cant reformat my other two hard drives (one ide one scsi) from NTFS (ur microsoft filth) to whatever partition is best. i have tried them all and put my own paths. (disk1 and disk2 respectivley) what am i doing wrong?

thankyou for your help
all criticizim is welcome

Joe

---

### Post by rck_hitokiri on 2006-08-13
hello. I what wierless card? please specify further... for playing your sounds you gotta go and read to this thread. It'll answer all your questions about sound and video. Hope this helps you. :D


[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

____________________________________________________
May the Penguin be with you.

---

### Post by John Q (be) on 2006-08-13
> **Joe of loath said:**
> ok most important first. i need drivers for my belkin wireless card. do they exist? it is a ummm F5D7000? that seems right.


[http://www.linuxquestions.org/questions/showthread.php?t=458657](http://www.linuxquestions.org/questions/showthread.php?t=458657)
is a disussion on going on an other forum maybe you can also monitor this too.

> **Joe of loath said:**
> second most important is i cannot play music files in rythmbox. they are all mp3, and i have set the cdrom drive (where all my music is stored :$) and urr it doesnt do anything. totem doesnt work either. 
The thing i'm now wondering is that are you settings correct?
meaning that are you running Xine?is alsa ok? and stuff like that...
commandline stuff like that isn't my best league so i hope that a more pro can give you appropriate commands

> **Joe of loath said:**
> and finally i cant reformat my other two hard drives (one ide one scsi) from NTFS (ur microsoft filth) to whatever partition is best. i have tried them all and put my own paths. (disk1 and disk2 respectivley) what am i doing wrong?
Joe
[http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183)
is a mentioned program for formattingstuff

John

---

### Post by Joe of loath on 2006-08-13
well im doing the driver installation now for the card. that other stuff is a bit over my head. xime? alsa? ppzz. anyway. thanks

---

### Post by John Q (be) on 2006-08-13
xine and alsa are kind of engines to handle your audio requests,...
(thats for so far i'd understand it)

If you can use the grapical interface (adept) for installing software you must search for xine and/or alsa and see if it's there.

than if it's present your programs for playing music must be configured as well.
In amarok for instance you must define your engine
(you can find it at *configure amaroK* (from one of the pull down menu's)

I can imagine that it must be similar for other programs...

John

---

### Post by Joe of loath on 2006-08-13
argh! It tells me to write sudo ndiswrapper -i <driver path>
i put it in like this: sudo ndiswrapper /usbdisk/belkin.inf
it says ndiswrapper isnt a command. do i need a plugin or something?](*,) ](*,)

---

### Post by wildseven on 2006-08-13
as for playing your mp3. you need to download the codecs from the repositories. try downloading easyubuntu.

---

### Post by Joe of loath on 2006-08-13
easyubuntu from where? do you have a mirror or site?

---

### Post by daou on 2006-08-13
For mp3's, you can get EasyUbuntu by copy/paste these lines in your terminal

```

wget http://users.on.net/~goetz/EasyUbuntu/current.tar.bz2
tar -xjf current.tar.bz2
cd EasyUbuntu
sudo python ./easyubuntu.in 
```

Then using EasyUbuntu install the codecs.

Or you can just install XMMS player from Synaptic and mp3's will work on Rhythmbox. But I recommend getting the codecs so you can play avi,wmv,mpg files etc.

---

### Post by Joe of loath on 2006-08-14
the problem is, xmms doesn't play mp3's and nor does rythmbox. and everytime i get a disk formatted it works until i reboot. this is so confusing! :confused:

---

### Post by davebgimp on 2006-08-14
> **Joe of loath said:**
> the problem is, xmms doesn't play mp3's and nor does rythmbox. and everytime i get a disk formatted it works until i reboot. this is so confusing! :confused:

As far as the MP3 playability, follow these steps to enable support for restricted formats:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

