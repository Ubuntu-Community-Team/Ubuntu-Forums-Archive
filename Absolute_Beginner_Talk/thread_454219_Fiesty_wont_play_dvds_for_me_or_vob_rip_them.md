---
title: "Fiesty wont play dvds for me or vob rip them"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Catfish81 on 2007-05-25
I've been trying to rip the VOBs off of DVDs for the past two days. I got vobcopy and it says:

> libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
libdvdread: Invalid IFO for VMGM (VIDEO_TS.BUP).
[Error] Can't open VMG info.


then I tried dvd::rip and it says:

> Error reading table of contents. Please check your DVD device setting in the Preferences and don't forget to put a DVD in the drive.

So now I tried with mplayer just playing the DVD and it says:

> catfish@delta:~$ mplayer dvd://
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 2700+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
libdvdread: Invalid IFO for VMGM (VIDEO_TS.BUP).
Can't open VMG info!
[file] No filename
Failed to open dvd://.


Exiting... (End of file)


The graphical version of mplayer is what I tried originally and it fails too. I don't know if I tried opening the DVD correctly with the console based mplayer. Graphical version says:

> Failed to open dvd://1

when I go to DVD -> Open Disc.


Err is there something wrong with my libdvdread or something? What packages do I need to play DVDs?

PS: I have rebooted too.
PPS: I have the drive mounted, correct paths etc. I can see the files on the DVD if I browse to it.

---

### Post by arochester on 2007-05-25
Are they encoded DVDs? Have you got libdvdcss2 loaded?

---

### Post by Praill on 2007-05-25
Just to elaborate:

```
sudo apt-get install libdvdcss2
```

---

### Post by viciouslime on 2007-05-25
> **Praill said:**
> Just to elaborate:

```
sudo apt-get install libdvdcss2
```

This will only work if you have the medibuntu repos enabled.

See: [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Catfish81 on 2007-05-27
Thanks for the replies. I installed libdvdcss2 and it worked. I did go looking for css packages but because that repository wasn't there I didn't find it.

---

### Post by Chet Hardin on 2007-06-23
Hey. I am having troubles playing DVDs as well. But I do have libdvdcss2_1.2.9-2 installed. Movie Player tells me I don't have the right plug-ins.  Any ideas?

Thanks.

---

### Post by anthonyp on 2007-06-23
I too get the same drama and have the above mentioned lib installed...

'Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
Please install necessary plug ins restart blablabla'

:(

---

### Post by SFCampbell on 2007-06-25
This generalized process has been very effective for me setting up multimedia playback and ripping on various different systems, both x86 and AMD64 bit kernels.  These steps are mostly specific to Feisty, but may still work on other versions or require little modification.

********EXECUTE COMMANDS IN TERMINAL WITHOUT THE QUOTATION MARKS********

First, add the following sources to your /etc/apt/sources.list file:

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main
deb [http://debian-multimedia.dfoell.org/](http://debian-multimedia.dfoell.org/) stable main
deb-src [http://debian-multimedia.dfoell.org/](http://debian-multimedia.dfoell.org/) stable main
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

Save and close, then run command "sudo apt-get update" a couple times in a terminal.
(As a habit, run "sudo apt-get upgrade" and "dist-upgrade" to ensure you have the latest system updates before continuing)

Next, install the multimedia packages as follows:
"sudo apt-get install w32codecs" for x86 installation (32bit) or "w64codecs" for AMD64.
"sudo apt-get install libdvdread3 libdvdcss2 libdvdnav4 xvid4conf"

Once this is done, run this command in a terminal:
"sh /usr/share/doc/libdvdread3/install-css.sh"

With these packages your Ubuntu installation should be able to read DVD video.  For reference, a complete list of packages available from Medibuntu can be found at [http://medibuntu.sos-sts.com/packages.php](http://medibuntu.sos-sts.com/packages.php)

Good luck all!

---

