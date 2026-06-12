---
title: "cant run the LIVE CD for 7.10"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Elotero on 2008-02-25
Trying to install Ubuntu 7.10 over XP since this morning. I seriously need some help. 

The laptop im trying to install it on is not that old but is giving me tons of problems. 

I boot the CD and it takes forever to load and finally i get an Orange screen with no icons. 

can someone walk me through a troubled process?? This is not an easy install. i suspect i may have to make BIOS changes but i dont want to blindly make these changes and screw up the entire system.

Please anybody can i get some help?

---

### Post by mkoehler on 2008-02-25
You shouldn't have to make any changes to your bios.  Can you please post some specs on your system, as that will help us to debug the problem.  Lastly, if you haven't already, you should try to run the disk check (from the startup menu).  This will run md5sum checks and check the integrity of the disk - sometimes your disk gets burned incorrectly.

---

### Post by Elotero on 2008-02-25
Thank you.

Okay this is a Fujitsu laptop. Intel Centrino/ 512 ram not sure what kind of motherboard.

Iwas originally trying to boot from the Official CD, the one you order for free. I ran a Check CD for errrors and it stated there was 2 errors so i just burned a new ISO and still running into trouble.

---

### Post by Sam Lars on 2008-02-25
Can you right click or press Alt+F2?  Or switch to Ctrl+Alt+F1, etc?

---

### Post by Elotero on 2008-02-25
Intel 1.70 ghz
L1 cache 64 kb
L2 cache 2048 kb

Total Memory: 512mb
Onboard 256 mb ddr sdram
memory slot 256 mb ddr sdram

I loaded in Safe graphics mode pretty smoothly into a completely black screen.

---

### Post by Elotero on 2008-02-25
> **Sam Lars said:**
> Can you right click or press Alt+F2?  Or switch to Alt+F1, etc?

Should i do this in Windows? Or on the BIOS startup?

---

### Post by Sam Lars on 2008-02-25
At the black screen try
Ctrl+Alt+F1
Do you get a terminal?

---

### Post by Elotero on 2008-02-25
checking integrity of the ISO i just burned... taking forever. This is so lame. I would expect problems like this on an old Gateway but not a newer laptop. I am stumped as to what is preventing me from installing.

---

### Post by ispy on 2008-02-25
if your sure you want it, just download and burn the alternate CD, it'll run faster, but you can't see if you like it from the live cd, and the installation is text based, not gui...

or use Xubuntu, it's faster... from there you can install Gnome, the only real difference between Ubuntu and Xubuntu...

---

### Post by Elotero on 2008-02-26
> **Sam Lars said:**
> At the black screen try
Ctrl+Alt+F1
Do you get a terminal?

Tried running Safe graphic mode and no. When it goes black and i use those commands i get no terminal. Somehow earlier i was able to get a terminal that read ubuntu@ubuntu...

---

### Post by Elotero on 2008-02-26
> **ispy said:**
> if your sure you want it, just download and burn the alternate CD, it'll run faster, but you can't see if you like it from the live cd, and the installation is text based, not gui...

or use Xubuntu, it's faster... from there you can install Gnome, the only real difference between Ubuntu and Xubuntu...

where would i DL an Alternate CD from?

---

### Post by ispy on 2008-02-26
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

right here, just check the box at the bottom that says "check here if you need the alernate desktop CD..."

and welcome!

---

### Post by Elotero on 2008-02-26
> **ispy said:**
> [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

right here, just check the box at the bottom that says "check here if you need the alernate desktop CD..."

and welcome!

since the installation is text based, can you help me setup? i just burned the Alternate CD.

---

### Post by Elotero on 2008-02-26
BTW booting from CD gets me to a black screen with a blinking cursor

---

### Post by Sam Lars on 2008-02-26
The alternate CD does?  Have you tried it a few times?  I've had weird problems with boots where it won't boot right a couple times before it finally works...

---

### Post by Elotero on 2008-02-26
> **Sam Lars said:**
> The alternate CD does?  Have you tried it a few times?  I've had weird problems with boots where it won't boot right a couple times before it finally works...

Okay i spoke too soon. Thank you by the way. The CD will eventuall take me to the menu where it asks if i want to text install, command line install, etc. I chose text install and quite a few items failed.  Install Base System failed. Is there some commands i can run to diagnose the problem?

---

### Post by Elotero on 2008-02-26
Can anyone help? So far i have tried to install/run the LIVE CD from ShipIT, Burned a copy from the Ubuntu website and also burned the alternate CD with no success. I have good faith that Ubuntu was meant to be for this laptop.

---

### Post by Elotero on 2008-02-26
BUMP

Please i am getting past the point of frustration to the point of desperation!

---

### Post by Sam Lars on 2008-02-26
I've had that happen too.  Have you tried it again and again?  Like I said about the graphics, it may eventually work.  The CD seems to be flaky and not always read right.

---

### Post by northern lights on 2008-02-26
If you can't get the Live CD to run, you could either try the Alternate CD (text-based installation):
[Alternate CD i386]("http://mirrors.gigenet.com/ubuntu/gutsy/ubuntu-7.10-alternate-i386.iso")
[Alternate CD 64bit]("http://mirrors.gigenet.com/ubuntu/gutsy/ubuntu-7.10-alternate-amd64.iso")

or, and I think this method's fab - saves you a CD also, you can install Ubuntu from the net:
[unetbootin]("http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411")
If you're currently running Windows, download the .exe, run, reboot & choose "Install Ubuntu".
If you're on some other distro, download the according file, run and all, same thing.

---

### Post by timbounceback on 2008-02-26
I'd recommend trying again. Or, if you manage to get to a command prompt when on the livecd, run
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by sneeks on 2008-02-26
i know this sounds silly,but have you tried burning the disc at 4x speed,this may help as i have found in the past,also if you have a spare drive(burner)give it a try as these things do go dud at times.
and on a final note,is it the cd image or the dvd,try the cd first as then you can still get all the repositries via the net.

---

### Post by kingtsy on 2008-02-26
Hi.

I had almost the same problem with my laptop. i can not install ubuntu on it. i tried maybe 5x and it wont installed until finally i try installing kubuntu and luckily it install.

after a few weeks of using kubuntu i try installing ubuntu live cd and guess what? It install in my laptop.

Hope this help.

Thanks.

---

