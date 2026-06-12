---
title: "Installing XGL &amp; Wine"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by bman on 2007-01-12
I finally have a computer with enough hardrive space and power to really do anything with linux. So these are the first 2 things I want to do.

Where do I get Wine & that XGL things...and how do I install it.


Thanks.

---

### Post by rj686 on 2007-01-12
[http://wiki.ubuntu.com](http://wiki.ubuntu.com) is very helpful :)

wine -> [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by bman on 2007-01-12
it says up repositories, which last time i tryed that it was very confusing...

the tutorial on those dont seem to help...

anyone got detail simple instructions on that..

---

### Post by rj686 on 2007-01-12
Dude go to

System > Software Sources to update your repos and make sure everything is checked :)

---

### Post by bman on 2007-01-12
everything is checked, now what

---

### Post by rj686 on 2007-01-12
Dude you really need to read. The how to I gave you explained it perfectly

---

### Post by AAM on 2007-01-12
BMAN,

firstly, you will need to do a lot of looking in the Forums (Fori) to get instructions.

_WINE_
Wine is installed from the Package Manager "Synaptic" found in the menu tree under **System|Administration|Synaptic Package Manager**. Start it up, click on one package you see and then type *wine*. You should see the wine package. [If not, you have to update your repository list to include the 4 repositories. The missing ones are usually Universe and Multiverse.] Select the package for install [right click] and then *Apply*.

OPening a terminal and typing **winecfg** will allow you to change some preferences, mainly which version of Windows you wish to emulate.

To run a EXE file, you open the terminal and type something like **wine MSWORD.exe**. Then you cross your fingers and pray like a saint that it will work! This is where it gets difficult, and you will need to root around the wine homepages to get more help.

_XGL_
This is more involved to get set up.

Step 1.

First you must (repeat MUST) have your graphics card working to give you hardware accelerated graphics. To check whether this is already running, open a terminal and type **glxgears**, you should see a small window with 3 gears turning. Leave it open for a while and something like this will appear in the terminal window:

```
9903 frames in 5.0 seconds = 1979.757 FPS
10853 frames in 5.0 seconds = 2170.523 FPS
```

To give you a benchmark, I am running an ATI Radeon 9600 card with acceleration. Without acceleration the number of frames per minute is substantially less (<500).

To get help with the hardware acceleration, search the forums. As a piece of friendly advice, write down your steps in case it is required again. Once I had worked out how to properly configure my card and XGL, I did a clean install and followed my orking instructions.

Step 2.
Now you can install XGL. This is dependent on your Ubuntu version and can be involved. But the instructions are out there.

---

### Post by fsando on 2007-01-12
I would recommend this for xgl beryl
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")
Its a good tutorial that in detail (with screen shots) explains adding repositories and gpg keys

BUT BEWARE I have experienced that the beryl related servers are not so reliable so have more than one ready (add or remove them depending on the response) and PAY ATTENTION to error messages - I spend almost three days reinstalling and pulling out hairs before heeding those error messages ;} and changed to a working server.

---

### Post by bman on 2007-01-15
alright well I got wine installed, and made sure its to emulate XP....

going to wait to do XGL...

How do I install XP, and programs under WINE?

---

### Post by majesticj on 2007-01-15
> **bman said:**
> alright well I got wine installed, and made sure its to emulate XP....

going to wait to do XGL...

How do I install XP, and programs under WINE?

You don't install XP per-se -- WINE isn't an emulator like Virtual PC.  It's a set of libraries that lets you run XP applications natively.

To install programs under wine, install them just as you would in Windows -- run their installers:

```
wine installer.exe
```

---

### Post by bman on 2007-01-15
so to use wine installer.exe does a install cd or whatnot have to be incerted, or what.

---

### Post by bman on 2007-01-15
anyone?...

---

### Post by inCursorated on 2007-01-15
you can run the wine installer.exe command from any directory that wine can "see"

to use a cd in wine you should open winecfg and assign a windows drive letter to the linux dir where your cd will be mounted (e.g., /media/cdrom)

---

### Post by inCursorated on 2007-01-15
.exe files should also have been associated with wine automatically. so, say if you download someinstaller.exe to your desktop you should be able to just click on it and wine will start the installer.

keep in mind that not all windows apps work perfectly (or at all) with wine. you should search the wine app db [here]("http://appdb.winehq.org/") first to see if it'll work.

---

