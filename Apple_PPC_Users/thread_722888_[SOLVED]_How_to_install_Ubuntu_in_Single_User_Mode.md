---
title: "[SOLVED] How to install Ubuntu in Single User Mode"
date: 2008-03-12
forum: Apple PPC Users
---

### Post by dtomas on 2008-03-12
I'm in the process of trying to install Ubuntu 6.10 on an Apple iMac G3.  I followed the instructions, found here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/22976](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/22976), on booting in single user mode and making a change in the xorg.conf regarding the HorizSync and VertRefresh as booting with Live CD boots to a black screen.

The above instruction allowed me to startx but when booted, there is only an icon for the CD on the desktop.  How do I begin the installation process from here?  I was expecting to see the Install icon on the desktop.

I've never done an install using terminal before and do not know where to begin.

Thanks in Advance for any information you may have.
-De

---

### Post by Gen2ly on 2008-03-13
not to shank ubuntu but the best bang for the buck is debian for PPC.   ubuntu doesn't officially support ppc anymore.  The ubuntu community does make a pretty good job of making a ppc version though the debianfolks are crafters of the art.

[http://www.us.debian.org/distrib/](http://www.us.debian.org/distrib/)

---

### Post by stream303 on 2008-03-13
> **dtomas said:**
> I've never done an install using terminal before and do not know where to begin.

No problem, although I'd suggest using a different Ubuntu,  Debian rocks, but there is no guarantee you won't run into the exact same situation there as well.  Unfortunately with ppc, just changing distros isn't always the magic bullet. :)

Let's gather some info:  What G3 iMac do you have?  Do you know how much ram is installed, and how large is the hard drive?  Do you want to preserve the old Mac-OS, or are you willing to do a clean wipe?  Do you have backup disks of the old Mac-OS?  This might help gather some info:

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

The reason for asking is that it I'd probably recommend the "alternate" text-based installer rather than use the Live-CD.  For your first install, I'd run Feisty 7.04, but another question is that you might like Xubuntu rather than Ubuntu, since Xubuntu runs a bit better with less ram.

So if you feel like downloading Ubuntu Feisty 7.04, you can get it here:

Be sure to grab the **"alternate"** powerpc install

[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

If you think you'd like Xubuntu Feisty 7.04, you can nab that here:
[http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/)

The fact that you can get to a commandline to do startx is a good sign!  Basically all we need to do after install is go back in, and change your /etc/X11/xorg.conf, which I'd be happy to walk you through.

---

### Post by dtomas on 2008-03-13
Dirk.R.Gently, thanks for the info.  I'll keep this in mind if all fails with Ubuntu.

Stream303,  I have an iMac G3 BondiBlue 233MHz with 384MB or RAM.  There is a 8GB HD.  The primary use of this computer will be for Web Browsing and Email.

And I'll be doing a clean installation.

So with this, how do we proceed?

Thanks Again,
De

---

### Post by stream303 on 2008-03-13
384 mb - that's fine.  Why not try the full Ubuntu "alternate" download?  You can always change it later if it still seems sluggish.

Due to the age of your machine, I'd recommend burning the downloaded iso image at a low speed, such as 4x.  Do not just copy it over to a cd.  If you need assistance with burning, the following howto is helpful:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

If you want to check the md5sum, remember that the ports we use don't have any md5sum hash entries in the suggested hash page.  Fortunately, you can find the md5sum hash at the top of the download directory as MD5SUM text file.

Basically, if you are burning from another Mac, just open disk-utility and drag your downloaded image to the left hand pane, highlight it, and hit the burn icon.  Choose a slow speed.  Note that some early versions of disk-utility may have had a bug where it fails to verify a properly burned disk, but in fact the disk is usable.

For windows, the only thing I have used, is IsoRecorder, which is mentioned in the howto.  You can go directly to it if you like from here:

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

A nice visual tutorial for it:
[http://isorecorder.alexfeinman.com/HowTo.htm](http://isorecorder.alexfeinman.com/HowTo.htm)

Once you have burned the cd, lets see if it will boot if you hold down the "C" key when booting.  Hopefully we'll be at a boot: prompt.

Please tell me that this isn't your one and only machine, otherwise we may end up in a chicken-and-egg scenario. :)

Let's see how that goes...

---

### Post by dtomas on 2008-03-17
Stream303,
Thanks for the pointing me to 'alternate' iso.  This worked without any hitch.  The only thing is that since my processor is a powerpc, i was limited to version 6.10.  Not a biggy for what the system will be used for.

Again, Thanks a bunch to everyone.

Deo

---

### Post by stream303 on 2008-03-17
Glad you got it up and running!

I just doublechecked those two links above, and if you feel like it, you should be able to run 7.04 with either Ubuntu or Xubuntu alternates on ppc.

Either way, I'm sure that Mac is much happier. :)

---

