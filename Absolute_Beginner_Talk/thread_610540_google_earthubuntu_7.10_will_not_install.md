---
title: "google earth/ubuntu 7.10 will not install"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by okkie on 2007-11-12
.is there any solution as yet?

---

### Post by Maestro23 on 2007-11-12
> **okkie said:**
> .is there any solution as yet?

Not sure what your problem is?  I installed GoogleEarth 4.2.1 on my Gutsy 64-bit machine last week.  Works just fine.  It's in the Repositories.

---

### Post by Dripbagulhos on 2007-11-12
> **okkie said:**
> .is there any solution as yet?

Hi okkie,

Please provide us more details... I have installed Google Earth from the original package in two machines, one using Ubuntu 7.10 32 bits and another usinf Ubuntu 7.10 64 bits. It was uneventfull in both.

Have you installed from the package of the offcial site?

[http://earth.google.com/](http://earth.google.com/)

---

### Post by okkie on 2007-11-12
i read a few places over the weekend the problem lies with the 32 bit download.it is a specific 7.10 problem and google must do something about it.

---

### Post by AlexenderReez on 2007-11-12
well...if somebody mention it,it doesn't necessarily you will get that problem...hm..i'm using google earth 32 bits in gutsy...works just fine....

have a look at -->


[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by oskar2000 on 2007-11-12
You still haven't told us what your problem is. I just downloaded and installed it after reading this. Took about 30 seconds, and is running as I write this.
No apparent problems.
Can you install it? What is the error? If you can you start it from the command line - what is the error?

---

### Post by okkie on 2007-11-13
finally installed ,screen comes up but it fails to initialise.must be something small.any ideas?

---

### Post by okkie on 2007-11-13
i now have it installed.screen comes up but it fails to initialise.should be something small.do you perhaps know?

---

### Post by z-bot on 2007-11-13
could you provide more details? what do you mean exactly by "fails to initialise" ?

---

### Post by Maestro23 on 2007-11-13
> **okkie said:**
> finally installed ,screen comes up but it fails to initialise.must be something small.any ideas?

Why are you making another thread about the same issue?

[http://ubuntuforums.org/showthread.php?t=610540](http://ubuntuforums.org/showthread.php?t=610540)

You need to more specific about the error if you want some help.

EDIT: Thanks to the Admin for merging the duplicate threads.

---

### Post by PartisanEntity on 2007-11-13
**Topics merged, okkie, 1 thread per topic please.**

---

### Post by okkie on 2007-11-13
to be more specific: i click on googleearth icon as usual.The google screen comes up and in the bottom tray it says initializing as usual but nothing further happens.the planet earth does not appear or should i say googleearth doesn't run

---

### Post by okkie on 2007-11-13
more specific.I now have googleearth installed on ubuntu 7.10.On clicking the icon googleearth screen opens and in the bottom tray it says 'initializing'.It seems to freeze here as planet earth doesn't appear.Idon't know how to get it running

---

### Post by brn on 2007-11-13
This is no help but I had a similar (or worse) problem. Running Gutsy on my desktop machine (1.3 GHz, 256 MB) everything is OK except Google Earth which briefly shows it's splash screen before crashing. --HARD--  I've tried installing it from the distro and the Google tar.gz with the same result.  Google Earth works fine on my somewhat newer laptop (Feisty, 1.8 GHz, 512 MB) so the only differences I can think of are Gutsy and the smaller RAM. I'm too lazy to reinstall Feisty and too cheap to buy more RAM.  Having this program on both computers isn't a high priority anyway but I've been using various Linux's for quite a few years and I'm not accustomed to seeing it crash.

---

### Post by okkie on 2007-11-14
Sorry For The Extra Thread,it Was Unintended.
I Found The Problem.google Cannot Read My Ati Radeon 9250 Card.iwill Make A New Thread To Try And Solve This.thanks All

---

### Post by peterroots on 2007-11-15
I've had a similar problem - I can download and install google earth but when it runs I get the splash screen and promptly logged out of my session.  I can log back in fine but that is as far as I can get.
any ideas on where to look on my system to find out what is going wrong?
I'm using Kubuntu (installed as 7.04 but has had all the updates going so far so not too sure what it counts as now!)

Just found instructions in another thread ([http://ubuntuforums.org/showthread.php?t=588962](http://ubuntuforums.org/showthread.php?t=588962)) that show how to install google from repositories rather than using a binary from the google site.
Just tried it out and it installed fine but still crashes my x server session

---

### Post by Dr@gonNoir1 on 2008-01-12
Hi,
I have the same problem, I installed Google Earth but the application just hangs. I did get some during installation here is the out put, any suggestions thanks.


daniel@testbox:~/Desktop$ sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...

---

### Post by garolou on 2008-02-26
Installing Google eath on Ubuntu 7.10 32 bit or 64bit
this is the procedure that worked for me:

Using GNU/Linux Firefox go to [http://earth.google.com/](http://earth.google.com/) and hit the download link. Don't try this in MS windows otherwise you will end-up with a MS binary.
Save the file to a folder of your choice. ( /tmp in this example)

Open a terminal
	Applications --> Accessories --> terminal
cd to that directory
	```
cd /tmp
```
make the file executable
	```
sudo chmod 740 GoogleEarthLinux.bin
```
run the install
	```
sudo ./GoogleEarthLinux.bin
```

Accept the default entries or change the path to ...
	```
/usr/local/google-earth/
```
to be more inline with Ubuntu conventions.
Leave the symbolic link as 
	```
/usr/local/bin
```
Hit the "begin install" button


For it to display properly on my system, I had to disable the visual effects
system --> preferences --> appearance --> Visual Effects --> none

Note to 64bit users: To run 32 bit applications, some libraries need to be installed. This may be the case here. If you have some problems running Google earth, install the 32 bit libraries:
```
sudo apt-get install lsb-core
sudo apt-get install ia32-libs
```
Start the application...
Applications --> Internet --> Google Earth

Cheers,
Dave
:-)

---

### Post by slugicide on 2008-03-01
I've tried installing Google Earth, but it always hangs on startup, even using the above instructions.  Including turning off desktop effects.  This is on a Dell E1505.

---

