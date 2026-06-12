---
title: "No sound on Beige G3 w/ 6.10"
date: 2007-03-09
forum: Apple PPC Users
---

### Post by Quither on 2007-03-09
I've got a 333MHz PPC Beige G3, running Ubuntu 6.10.  Sound does not work at all.  If i try to change the system volume, it tells me it cant find my sound card, or i dont have GStreamer installed.  Can anyone help me out here?

---

### Post by Quither on 2007-03-12
anyone have any ideas here?  I would really like to get this working!

---

### Post by Tommy on 2007-03-14
> **Quither said:**
> anyone have any ideas here?  I would really like to get this working!

I'd like to know if you had to pull any strange tricks to get the installer kernel to boot. Was this a clean install from a 6.10 disk, or upgraded from an earlier version?

I ask because I have a PowerMac 9600 (similar age to your Beige G3) that I have just about given up on. I got a live CD to boot once, but the sound was very diminished -- you could tell there was sound but it was so faint as to be unusable. But I couldn't get the installer disk to put it on the hard drive -- it failed when it was trying to detect the CD ROM. I downloaded all the versions of the CD -- the server, the Alternate AND the live desktop, and if I remember right, the live was the only one I could boot.

Actually, now that I think of it, I didn't try INSTALLING from the Live CD AFTER I booted.... I don't know that I even looked. It's been a few weeks ago so I'll have a look again soon.

---

### Post by Quither on 2007-03-15
nope... no tricks.  I installed from the install CD... the only oddity is that i use BootX (need to, it's an old word mac) to boot linux.

---

### Post by Tommy on 2007-03-15
Yes, I'm very familiar with BootX -- I'm typing this on a Wallstreet... A few weeks back I tried everything to get the PowerMac 9600 to go, and my notes indicate I got the liveCD and the CD check going, but could not install. It would fail when trying to detect the CDs.

BUT on this particular beast I added a controller card for cheap (non-SCSI) disks. I believe your Beige G3 can handle ATA disks already, so I may just be tripping up on this unusual PCI card.

---

### Post by Quither on 2007-03-29
Here is a screenshot of the error im getting.  If anyone cna help with this, i'd really appricate it.  :confused: 

[Click here for screenshot](http://img256.imageshack.us/img256/5044/screenshotix5.png)

---

### Post by Tommy on 2007-03-30
I see the error message refers to missing gstreamer plugins... I'm trying to remember if gstreamer is one of the applications affected by the altivec detection bug. [https://launchpad.net/ubuntu/+source/ffmpeg/+bug/74282](https://launchpad.net/ubuntu/+source/ffmpeg/+bug/74282)

I know the bug affects ffmpeg and mplayer. The problem affects PowerPC G3 processors (and presumably any other PowerPCs that don't have Altivec). As a user, it means several standard multimedia packages simply fail on G3 systems.

The good news is there has been a patch submitted, and if folks like it, it will ultimately get fixed. The bad news is only a few G3 systems are supported by Ubuntu (which only supports newworld), so the fix will probably have to filter downstream from Debian.

AH here's some support for the theory -- a Debian bug complaining that GNOME doesn't work on oldworlds [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=404876](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=404876)  -- the speculation is it's the same problem.

---

### Post by Quither on 2007-03-30
:mad:
so... im screwed untill a patch comes out?  dang.

Is this just an issue w. v6?  or with all versions of U?

---

### Post by Tommy on 2007-03-30
> **Quither said:**
> :mad:
Is this just an issue w. v6?  or with all versions of U?

I don't remember hearing of it until 6.06 Dapper, but it obviously affects more packages in 6.10. (I'm still on Dapper on my PowerBook Wallstreet, and I haven't had trouble with GNOME, though I don't use it much. There ARE things that don't work -- ffmpeg and other video things, for instance -- but the ALSA sound controls work, mostly.)

I wish I had a solid recommendation -- a G3 ideally needs patched and recompiled versions of several libraries to avoid the Altivec detection. Otherwise, avoiding the problematic packages would be all you could do.

In the meantime you MIGHT try installing the Kubuntu and Xubuntu packages and see if more of those work. I run all of them on my Wallstreet with Dapper 6.06 -- it's easy to switch among the different desktop environments with each login. :)

---

