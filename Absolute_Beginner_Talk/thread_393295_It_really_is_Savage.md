---
title: "It really *is* Savage"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by StarscreamD on 2007-03-25
Kubuntu Feisty user.. I upgrade all the time. My system is a 1.3 Ghz Celeron with 512 mb of SDRAM and a NViDiA GeForce MX 420 graphics card.

Question: I am trying to install Savage: The Battle for Newerth from this site. [http://www.s2games.com/savage/downloads.php](http://www.s2games.com/savage/downloads.php)

I downloaded and ran this version, located in the link above.
SEP Package Primary Download Location (Linux)
 [http://www.happypuppy.com](http://www.happypuppy.com) < 2.00e Linux Retail + SEP3T

The install seems to have executed perfectly. Now, when I attempt to run the game from terminal, a black screen displays for several seconds, and then a string of errors spits out.
```
silverback.bin: ../../src/xcb_lock.c:62: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
./Savage: line 21:  5782 Segmentation fault      (core dumped) LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin
```

The top two lines are repeated many times before the bottom two lines display. What's goin' on here? Can I install this game on Ubuntu? Thank you everyone!

UPDATE: I just installed Neverwinter Nights, and when I run *that* executable, I get a similar error.
```
nwmain: ../../src/xcb_lock.c:62: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
./nwn: line 10: 16939 Aborted                 (core dumped) ./nwmain $@
```

Man, I really want this issue resolved this weekend so I can get into some high-quality gaming. Anyone else having these issues? Thanks everyone!

---

### Post by carlosfocker on 2007-03-26
Try this post [http://www.ubuntuforums.org/showthread.php?p=2345992](http://www.ubuntuforums.org/showthread.php?p=2345992)

---

### Post by StarscreamD on 2007-03-26
Yeah so I got NWN working, that's good. I read several other forum posts, but I could not find an answer to this problem. Something display related I suspect. When I run Savage(full install with SEP3T) from a shortcut, a black screen displays for a moment and then I am spewed out into the desktop.

In terminal, the same thing happens and this error comes up:

> System_Init()
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xc1
  Serial number of failed request:  104
  Current serial number in output stream:  106


I'm almost there! Throw me a bone people! Thank you for your help.

---

### Post by carlosfocker on 2007-03-27
Do you have and ATI card? Try the following in your xorg.conf under where the modules are loaded( Load "glx", Load "dri")( Make sure you back up this file, I put it im my instructions) I'm gonna try to pick apart the message a little more but the program is obviously passing a value to an int for a video setting that is not compatible with your system.

```

sudo cp sudo /etc/X11/xorg.conf /etc/X11/xorg.confbackup

```
```

sudo gedit /etc/X11/xorg.conf

```
Add this to Xorg.conf
```

SubSection "extmod"
     Option "Omit XFree86-VidModeExtension"
EndSubSection
```

---

### Post by Lord Illidan on 2007-03-27
He does not have an ATI card.

> ubuntu Feisty user.. I upgrade all the time. My system is a 1.3 Ghz Celeron with 512 mb of SDRAM and a **NViDiA GeForce MX 420 graphics card**.Please, read questions properly before suggesting answers.

---

### Post by carlosfocker on 2007-03-28
So sorry to the above poster. 

Have you run the using sudo? Some people have had problems running savage without being a su.

```
sudo ./Savage
```

If not try this out go it from [http://forums.s2games.com/showthread.php?p=34700](http://forums.s2games.com/showthread.php?p=34700)

Go to your /Savage/game folder, there should be a "startup.cfg" file. If not, create one yourself.

Change the following line (Or add it if it's not there):

```
setsave vid_mode #
```

(Where # is any number) so that whatever that # is corresponds to a number in the "Adding Mode" section of the log you posted above. So, to change it to 1024x768x16, you would change the line to:

```
setsave vid_mode 9
```

---

### Post by Perfect Storm on 2007-03-28
Savage installation guide: [http://gaming.gwos.org/e107_plugins/content/content.php?content.61](http://gaming.gwos.org/e107_plugins/content/content.php?content.61)

---

### Post by StarscreamD on 2007-03-28
I'll attempt your suggestions and post back with the results shortly. Thank you for the assistance so far everyone.

---

### Post by StarscreamD on 2007-03-28
Uhm, something weird happened. I am getting the first error again after updating/upgrading!

[https://launchpad.net/ubuntu/+source/libxcb/+bug/92294](https://launchpad.net/ubuntu/+source/libxcb/+bug/92294)

This seems to have been reported and you can get around this in NWN, can someone explain how I can get around this in Savage? Thank you!

```
silverback.bin: ../../src/xcb_lock.c:62: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
./Savage: line 21:  5782 Segmentation fault      (core dumped) LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin
```

---

### Post by StarscreamD on 2007-03-29
Artificial Intelligence:

I uninstalled and then reinstalled Savage using your faq listed above.

Firstly, alacarte was a nightmare. It was giving all sorts of errors and I can edit the menus and make a shortcut with what I got. I am using kubuntu however, and I noticed some of what you would have me install is gnome(gnome-menus & libgnome-menu2). Perhaps this is why alacarte was incompatible with my system. The GUI would appear, but on any command a slew of python errors came up. I installed by aptitude, so I dunno why it didn't work for me.

Secondly, your faq, while it may be useful to some, did not solve my problem. I think because of the launchpad bug report that I saw that it will be fixed in an update eventually, is this assumption correct? What is up with libxcb not working after an update all of a sudden? Again, this is the error message I am receiving.
```

silverback.bin: ../../src/xcb_lock.c:62: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
silverback.bin: ../../src/xcb_lock.c:62: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
./Savage: line 21:  7245 Segmentation fault      (core dumped) LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin `pwd`
```

NWN works fine at this point, but I had to do a little code editing. Had to do with libxcb, see what I mean-

[http://www.ubuntuforums.org/showthread.php?t=391550](http://www.ubuntuforums.org/showthread.php?t=391550)

This again, is the bug report that parallels my issue.

[https://launchpad.net/ubuntu/+source/libxcb/+bug/87390](https://launchpad.net/ubuntu/+source/libxcb/+bug/87390)

I guess I could always revert to the previous release...?

---

### Post by Perfect Storm on 2007-03-29
Well, the howto havn't been tested in feisty as I always stay with stable release.

The alacarte issue is that it's written with gnome in mind, so if you're using KDE you just uses the information provided to the KDE launcher instead of running alacarte (gnome thing)

Also when doing a clean install wipe ~/.Savage in your home folder.

---

### Post by StarscreamD on 2007-03-29
I just used the uninstall script in the ~/.Games/Savage dir, and then deleted that dir. Also, I did delete the hidden dir in the ~/ folder. Still having the same problems. What do you make of all this AI?

---

### Post by Perfect Storm on 2007-03-29
Not much than it's already been said, that the lib files is bugged in feisty.

---

### Post by StarscreamD on 2007-03-29
I found a work-around for this issue. Install this to any directory, it is a stand-alone version of Savage.

[http://www.notforidiots.com/SFE/SFE-Standalone.tar.gz](http://www.notforidiots.com/SFE/SFE-Standalone.tar.gz)

Just un-tarball and run savage.sh. Runs like a dream!

---

### Post by olejorgen on 2007-05-22
> **StarscreamD said:**
> I found a work-around for this issue. Install this to any directory, it is a stand-alone version of Savage.

[http://www.notforidiots.com/SFE/SFE-Standalone.tar.gz](http://www.notforidiots.com/SFE/SFE-Standalone.tar.gz)

Just un-tarball and run savage.sh. Runs like a dream!
Does not work here... I get to initialization.... Then EVERYTHING hangs. (ie. system dies completely)

:(

---

### Post by s_spiff on 2007-09-13
Tried the standalone, but gettin the following output. someone help me out. I'm o AMD64, Feisty Fawn and a Nvidia graphic card, drivers installed using Envy.
```
cdspiff@spiffed:~$ cd Setups/Games/
spiff@spiffed:~/Setups/Games$ cd Savage/
spiff@spiffed:~/Setups/Games/Savage$ ./savage.sh 
./silverback.bin: error while loading shared libraries: libcom_err.so.2: cannot open shared object file: No such file or directory
spiff@spiffed:~/Setups/Games/Savage$ 
```

---

### Post by Perfect Storm on 2007-09-13
I wrote a guide for Savage FE version: [http://gaming.gwos.org/doku.php/guides:savage](http://gaming.gwos.org/doku.php/guides:savage)

note it's tested on 32-bit, nvidia, festy

---

