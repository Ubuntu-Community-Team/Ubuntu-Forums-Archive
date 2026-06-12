---
title: "Installation on Ibook doesn't proceed"
date: 2008-05-19
forum: Apple Hardware Users
---

### Post by Datur on 2008-05-19
Dear Ubuntu users,

I'm trying to install Ubuntu 8.04 PPC on my G3 iBook with 386MB memory and 30GB harddrive. The LiveCD and installation starts ok, but the process jams after clicking on the Forward button on 'Who are you' screen. At this point the the pointer turns into the'Busy wheel' and nothing happpens anymore (but otherwise the system works, and I can about the installation by closing the window).

Any ideas what's going on? Is there a way to get more verbose log or something to figure out what's exactly going on when the jam happens?
 
The funny thing is that at first time installation proceeded almost to the end, but stopped at 'Installing Yaboot' stage (94%, when looking for other operating systems). The behaviour described above started after this unsuccesful installation.

Somehow I suspect that the problem might be related to the partitioning of the hard drive, because the GParted won't start properly after unsuccesful installation, but keeps scanning the partitions. (I might be completely wrong of course) 

The current partition looks bit messy to me (long time ago I tried some sort of Linux installation), first there is many very small partitions (don't know if these are necesssary, maybe they have something to do with Mac OSX booting?), then empty 6GB partition, 17GB MacOSX 10.3.9 partition (this one still boots ok), 0.5GB linux swap and in the end 5GB empty space).

First I tried to install Ubuntu on the empty 6GB partition, in order to have a dual boot system, by using the guided partitioning on the largest free space option. Later I tried the guided partitioning on the whole harddrive. Both options result on the same jam, and the MacOSX still boots!

I'd be grateful for any help!! :confused:

---

### Post by stream303 on 2008-05-19
Which G3 iBook do you have?
[http://www.everymac.com/systems/apple/ibook/index-ibook.html](http://www.everymac.com/systems/apple/ibook/index-ibook.html)

I'd recommend trying the "alternate" installer but I think your drive has some unused partitions taking up space.

If you feel up to it, and have the original OSX install disks, have backed up all your data, you might consider starting fresh since you have all those old partitions laying around from an earlier Linux installation attempt.

If you don't like OSX, you could just "use the whole disk" when doing guided partitioning with Ubuntu.  Of course, this will wipe out the whole drive.

Or perhaps you could reinstall OSX, but first cut the drive in half by using OSX disk-utility to repartition the drive and reinstall osx onto the first partition, and then let Ubuntu install to free space afterwards...

As always, YMMV, but getting experience reinstalling OSX isn't always a bad thing, but consider the risk if you aren't up to the task....

---

### Post by Datur on 2008-05-26
Thanks for your help, stream303!

My iBook is iBook G3/700 (16 VRAM - Tr), I think.

Does the alternate CD install X, Gnome etc. as well, or only command line interface? I wouldn't want to get into doing all the paintaking configuring myself!

I did try the use whole disk option in the LiveCD Guided partitioning, but the installation freezed just the same!

---

### Post by stream303 on 2008-05-26
The "alternate" will install a fully graphical system, but during the install itself, relies on simple text and vga-style graphics.  This reduces the memory requirements needed to install, and sometimes overcomes graphical quirks in the live-cd installer.

After your first reboot, the system should come up with full Gnome etc.  Sometimes however, we need to apply a little tlc at the comandline. Not always, but just be prepared. :)

---

### Post by Datur on 2008-06-14
Hello, and thanks again. I finally had time to try installation again, and it worked ok with the alternative CD!

However, sound doesn't work at all. Apparently the sound device is not installed at all:

```
~$ cat /dev/sndstat 
Sound Driver:3.8.1a-980706 (ALSA v1.0.15 emulation code)
Kernel: Linux rikkaruusu 2.6.24-18-powerpc #1 Wed May 28 19:29:28 UTC 2008 ppc
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
--- no soundcards ---

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers: NOT ENABLED IN CONFIG

```

Unfortunately, I have no idea how to fix this. It's probably something simple, because sound did work from the LiveCD!

Any ideas?

---

### Post by mchladek on 2008-06-14
Try adding the following to /etc/modules:

```

snd-powermac

```

I had the same problem when installing on my iBook G4 from the alternate CD.  This did the trick.

---

### Post by Datur on 2008-06-14
Yes, it did the trick, thanks a lot! :)

Now, if I only would manage to make suspend (sleep) to work, I'd be very happy with the system. Closing the lid does nothing, and suspend from the menu only locks the computer. Maybe I'll find something on the forums!

---

### Post by stream303 on 2008-06-14
Congrats on the install!

Have you seen the nice addition to the known-issues faq in regards to suspending:

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-5cdcb8ed2e1c81fb49e0f22782bf67c86d911ca7](https://wiki.ubuntu.com/PowerPCKnownIssues#head-5cdcb8ed2e1c81fb49e0f22782bf67c86d911ca7)

Btw, don't forget to see if you prefer subpixel smoothing for your fonts, especially with an lcd:

System > Preferences > Appearance > Fonts > Subpixel smoothing

---

