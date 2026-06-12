---
title: "Issue with installing Ubuntu"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by newbie2linux on 2006-07-20
Hello there i am a newbie lol, i just bought a Acer T-135 Aspire computer that has a AMD 3100 chip on it, i tried running the Live CD (Version 5?) and it wouldnt allow me to run the live CD, the only message that i could see what related to the AMD chip and/or something about the graphics are not supported, can anyone help me it would be greatly appreciated :KS

---

### Post by adam.tropics on 2006-07-20
Could you have another go, and perhaps be a little more specific. Plus what video card are you using?

---

### Post by newbie2linux on 2006-07-20
here is the chipset info 
AMD Sempron™ Processor 3100+
(256KB L2 cache, 1800MHz, 333MHz FSB)

VIA UniChrome S3 DDR

sorry if this is not totally informing i dont have access to my system at the moment kinda going on memory and what the specs are from the acer website :( 

when i was running the Live CD it seemed to go ok then when it got to the hardware/graphics section it just stopped it went to the command line interface (I think) then i couldn't go anywhere i had to take out the CD in order to get back into the Windows XP

---

### Post by adam.tropics on 2006-07-20
No worries. When you run the live cd and it 'stops' it should with a little luck be the command line. Type in
```

sudo dpkg-reconfigure xserver-xorg
```

then press enter

Follow through (defaults are fin for most of it) and in the driver bit, select 'via' if it's there, else 'vesa' if it's not. When it's done, at the command line type

```
startx

```
enter

---

### Post by newbie2linux on 2006-07-20
Thanks alot i appreciate this :D i did manage to try out the live CD on two other computers and was totally amazed with it :D I am hoping to get the newest version and install it on to my computer what kind of things can i do with Ubuntu? i have a few ideas i would like to pursue (creating my own internet radio station would be very shiny) have any insights? thanks again i will try it out

---

### Post by adam.tropics on 2006-07-20
> **newbie2linux said:**
> Thanks alot i appreciate this :D i did manage to try out the live CD on two other computers and was totally amazed with it :D I am hoping to get the newest version and install it on to my computer what kind of things can i do with Ubuntu? i have a few ideas i would like to pursue (creating my own internet radio station would be very shiny) have any insights? thanks again i will try it out

What a HUGE question! No single answer, except use your imagination! You can create an online radio station with any os at [http://www.last.fm](http://www.last.fm) and they can be listened to in Amarok (with a plugin!)

For a pretty 'excited' guide to installing Ubuntu [this video]("http://enterprise.linux.com/enterprise/06/07/05/1533204.shtml?tid=23") from linux.com is pretty neat. They also have other Ubuntu videos explaining how to update software etc etc, so probably worth a look.

---

### Post by newbie2linux on 2006-07-21
greetings again, i just finished trying to run the Live CD of Ubuntu Version 5.04 on my Acer system, not everything went according to plan, i tried those steps you suggested and was finally able to get to the desktop however several other items were not functioning correctly ( i used 2 seperate CD's for this)

1. load installer components from CD-failed
2. integrity check failed
  ./pool/main/l/linux-source-2.6.10/nic-extra-modules-2.6.10-5-386-
di_2.6.10-34_i386.udeb failed MD5 checksum
3. unavailable modules & devices
   ide-mod (Linux IDE driver)
   ide-probe-mod
   ide-detect
   ide-floppy
These were the error messages i recieved on the first CD, i was able to get to a login screen however couldnt get anywhere after that ](*,) I have used these disks on two other computers with no problems

2nd Disk 

1. No Ethernet Card detected (supported?)
2. Cannot detect CD-ROM device(????)
3. was able to get into the main desktop screen, program windows were too large for the screen couldnt see most of the window attempted to change screen resolution using the software as well as the manual options for the monitor b4 allowing me to the main screen it said that there would be problems with the GNOME desktop and if i wanted to change the settings(?) to go to file/etc/hosts. ](*,) 

My system specs are AMD Sempron 3100+ chip
in sysinfo it states that it is X-86 based PC 

Can ANYONE help?

---

### Post by newbie2linux on 2006-07-21
greetings again, i just finished trying to run the Live CD of Ubuntu Version 5.04 on my Acer system, not everything went according to plan, i tried those steps you suggested and was finally able to get to the desktop however several other items were not functioning correctly ( i used 2 seperate CD's for this)

1. load installer components from CD-failed
2. integrity check failed
./pool/main/l/linux-source-2.6.10/nic-extra-modules-2.6.10-5-386-
di_2.6.10-34_i386.udeb failed MD5 checksum
3. unavailable modules & devices
ide-mod (Linux IDE driver)
ide-probe-mod
ide-detect
ide-floppy
These were the error messages i recieved on the first CD, i was able to get to a login screen however couldnt get anywhere after that I have used these disks on two other computers with no problems

2nd Disk

1. No Ethernet Card detected (supported?)
2. Cannot detect CD-ROM device(????)
3. was able to get into the main desktop screen, program windows were too large for the screen couldnt see most of the window attempted to change screen resolution using the software as well as the manual options for the monitor b4 allowing me to the main screen it said that there would be problems with the GNOME desktop and if i wanted to change the settings(?) to go to file/etc/hosts.

My system specs are AMD Sempron 3100+ chip
in sysinfo it states that it is X-86 based PC

Can ANYONE help?

---

### Post by nalmeth on 2006-07-21
Did you say 5.04? That's hoary, 2 versions old. Can you grab a newer image? Your first disc was definately corrupted.

Newest version is 6.06 Dapper Drake

---

### Post by newbie2linux on 2006-07-21
which one would i download? i dont know enough about linux OS's to determine what is compatible with my system, i would really like to install Ubuntu on my system :D

---

### Post by orb9220 on 2006-07-21
this is the link to download the Ubuntu 6.06 LTE "Dapper" cd disk image.

Just select the server closest to you.
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Hope this helps

---

### Post by Sef on 2006-07-21
> which one would i download?

I would download this one:

> PC (Intel x86) desktop CD
    For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows. Choose this if you are at all unsure.

[Download]("http://mirror.cs.umn.edu/ubuntu-releases/6.06/")

---

### Post by newbie2linux on 2006-07-21
i appreciate the link, i checked the list and there are lots of options to choose from, out of all of those listed there which one do i get?](*,)

---

### Post by K.Mandla on 2006-07-21
Also make sure you're donwloading the "i386" version. If you grab the Apple version by mistake, nothing will work. ;)

EDIT: This is the name of the installer disk for x86 machines (like yours)...

```
ubuntu-6.06-alternate-i386.iso  
```
This is the "desktop" CD, which boots to a temporary system you can try out before installing.

```
ubuntu-6.06-desktop-i386.iso 
```

---

### Post by orb9220 on 2006-07-21
Yes that is the same link mine is just one page up from that to let you chose which server to use so you can select the server in your country.

Just pick the one like he said which is the first one and save to folder desktop or where you prefer.

Then burn the iso and boot with it.

Hope we cleared up some of the confusion.

---

### Post by newbie2linux on 2006-07-21
more silly questions lol when i click on the alternate link for the newest version it states that it is a WinRAR archive, i thought these were ISO files?:confused:  probably missing something here lol thanks for your patience

---

### Post by swamytk on 2006-07-21
If you have system of PIII/256MB or more:
right click the following links and select "Save Link as", save this ISO file and burn to CD.
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-i386.iso](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-i386.iso)
  
If you have older system than PIII/256MB:
right click the following links and select "Save Link as", save this ISO file and burn to CD.
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-i386.iso](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-i386.iso)

---

### Post by newbie2linux on 2006-07-21
also altho i have tried the LIVE CD i didnt get a whole lot of time to check out all the tools and functions, hows the user friendliness of Ubuntu (tru Noob lol)

---

### Post by newbie2linux on 2006-07-21
Miigwiich (Thanks) for the advice guys i appreciate it :-D  I hope to be a Ubuntu afficando soon :D

---

