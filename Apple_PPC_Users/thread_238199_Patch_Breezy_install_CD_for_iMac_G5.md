---
title: "Patch Breezy install CD for iMac G5?"
date: 2006-08-17
forum: Apple PPC Users
---

### Post by buglord on 2006-08-17
I've seen here that several people have attempted to install Dapper on their iMac G5, and that the boot process invariably hangs.
This is supposed to be because of the audio module loaded in the default kernel.

My question is: how difficult would it be to build a new kernel image and patch it into the install CD? I've read that the kernel version 2.6.17 works well with the iMac G5.

---

### Post by buglord on 2006-08-18
bump

---

### Post by stmiller on 2006-08-18
Where does it hang? Have you tried the 'alternative' cd? This installs in text mode. If this text install process goes well, while the system is still running from that live cd, you could fetch a current kernel from kernel.org and compile it before the initial reboot. Then reboot into your new kernel. Though this is sort of deep.

On gentoo.org, imac G5 works fine with gentoo ppc. And they have been using kernels previous to 2.6.17. Search there on their ppc forum section for some more help, perhaps.

---

### Post by buglord on 2006-08-18
Good to know that the alternative installer uses a text installer.

I should be able to manage compiling an alternative kernel.

Thanks for the tips!

---

### Post by turnkit on 2006-08-24
I'm having hanging on a slot-loader iMac 333Mhz using Kubuntu Alternate (text only)

It hangs at different places.  But in the same stage... I think it said 'unpacking bash' and just got stuck at 6% (or 4%) after unplugging and trying again it got stuck at 46% while installing something.

I can still get a console window and do a ps etc. but for some reason it just went to lunch.
---
I wonder about the media quality.  The PC version has a cool media check feature which would be nice.
--
I can't install any of these to the 233Mhz machines since they are so picky about CD-R's.  I am not sure how to burn a disc that will read.  Very bummed that you can't order xubuntu / edubuntu / kubuntu alternate on pre-pressed CD's since these actually read OKAY on an older tray loading iMac 233Mhz.

Any suggestions on media brands to use that iMac 233Mhz will read okay?  (I have been burning as slow as the burner will allow.)

---

### Post by turnkit on 2006-08-24
woo woot!

my hanging problems were solved (so far)!

the problem?  cheap media!

I took my cheap media CD-R w/ xubuntu alt and duplicated it with Nero on an XP machine.  I copied to a TDK quality CD-R on a DVD-R/CD-R combo drive.  The slowest speed I could burn was 16x (and that's what I used.)

Now my slot loader 333Mhz iMac boots xubuntu alt from this TDK CD-R w/o a problem.  

(I am assuming the hanging I was experiencing w/ the *kubuntu* alt was related to the same cheap media that wouldn't even let me boot to the xubuntu alt which now works fine.  This is a big assumption, but this I do know for certain... I couldn't boot with a cheap CD-R and after duplicating from that same cheap CD-R to a TDK CD-R I can boot just fine... I've yet to see if the tray loading 233Mhz iMacs will read this new burn.:p )

---

### Post by Torrance on 2006-08-25
> **buglord said:**
> Good to know that the alternative installer uses a text installer.

I should be able to manage compiling an alternative kernel.

Thanks for the tips!

Any results regarding a kernel recompile? There are two links that may be of help:
[http://ubuntuforums.org/showthread.php?t=232908](http://ubuntuforums.org/showthread.php?t=232908)
[https://wiki.ubuntu.com/iMacG5revC](https://wiki.ubuntu.com/iMacG5revC)

Also, the bug for this is filed at [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/23445](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/23445), so please post any success AND failures you have. Cheers! :D

---

