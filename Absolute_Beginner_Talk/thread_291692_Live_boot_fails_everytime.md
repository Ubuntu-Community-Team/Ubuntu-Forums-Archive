---
title: "Live boot fails everytime"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by leavingOS2 on 2006-11-02
Everytime I attempt to live boot, it freezes on "mounting root file sys."  I'd like to live boot before installing it for the first time.

I have a Pentium III 500mhz with 750MB ram, Adaptec 2940U2W and 2 SCSI HD which currently boots with IBM's Boot Manager.  I have  an IDE cdr (a bit old--2X).

Any other info needed to get some advice/tips in getting live booted?

I'd like to migrate to Linux after 14 years with OS/2.  I've got experience with multi-boot partition strategies using various versions of Windows, multiple OS/2 boot partitions, FAT32, NTFS, HPFS and OS/2's implementation of JFS.  I installed linux once 7 years ago, but the learning curve was too high for me at that moment, but I'm fed up with MS and OS/2, so I'm going to do it this time.

I've chosen Ubuntu.  I figured I'd live boot before rearranging partitions (I think I've got 8 now, and a new 73GB harddrive to add to that).

Thanks

---

### Post by floridauser007 on 2006-11-02
> **leavingOS2 said:**
> Everytime I attempt to live boot, it freezes on "mounting root file sys."  I'd like to live boot before installing it for the first time.

I have a Pentium III 500mhz with 750MB ram, Adaptec 2940U2W and 2 SCSI HD which currently boots with IBM's Boot Manager.  I have  an IDE cdr (a bit old--2X).

Any other info needed to get some advice/tips in getting live booted?

I'd like to migrate to Linux after 14 years with OS/2.  I've got experience with multi-boot partition strategies using various versions of Windows, multiple OS/2 boot partitions, FAT32, NTFS, HPFS and OS/2's implementation of JFS.  I installed linux once 7 years ago, but the learning curve was too high for me at that moment, but I'm fed up with MS and OS/2, so I'm going to do it this time.

I've chosen Ubuntu.  I figured I'd live boot before rearranging partitions (I think I've got 8 now, and a new 73GB harddrive to add to that).

Thanks

Hello!

I know it probably is not what you'd expect but check the CD.  run the self test and the memory test.  If you cannot get that far, burn an ISO again and use the lowest speed possible.  Also if you can perhaps try one of those CD drive cleaning disks that you can buy for $10.

When I installed I had a problem like yours except the liveCD portion worked great.  It was the install that failed.  It turned out after cleaning the CD, it installed fine.  I do not think the LiveCD or the installer are very tolerant of defective media or CDrom drive problems.

I think you'll love Ubuntu when you finally get it to boot.  I used to use linux back in 2000 myself and have been VERY impressed with how much easier it is now.  Hang in there!

Also I recommend Dapper over Edgy right now.  Especially since you are new....

---

### Post by leavingOS2 on 2006-11-02
Thanks for the suggestions.  I have downloaded the iso 3 times, twice on my computer (winxp partition) and burned it with my old cdr 2x max speed writer, and a third time with another w2k machine with a recent 52x writer (written at 24x).  After 3 tries, I was hoping that wasn't the problem.

I was wondering if the old 2x cdr is causing a problem with the install (dirty or incompatible??).  I'm considering running out and getting a brand new cdrw/dvdrw see if that helps.  The old cdr does boot other cds reliably (e.g., partition magic, os/2 installation cds).

I happened to download 6.06 the day before 6.10 was posted so that's what I got, and I agree, that's what I'll stick with.

Thanks again.

---

### Post by floridauser007 on 2006-11-02
> **leavingOS2 said:**
> Thanks for the suggestions.  I have downloaded the iso 3 times, twice on my computer (winxp partition) and burned it with my old cdr 2x max speed writer, and a third time with another w2k machine with a recent 52x writer (written at 24x).  After 3 tries, I was hoping that wasn't the problem.

I was wondering if the old 2x cdr is causing a problem with the install (dirty or incompatible??).  I'm considering running out and getting a brand new cdrw/dvdrw see if that helps.  The old cdr does boot other cds reliably (e.g., partition magic, os/2 installation cds).

I happened to download 6.06 the day before 6.10 was posted so that's what I got, and I agree, that's what I'll stick with.

Thanks again.

Well I'm no expert just a user trying to help too, but it sounds like it is unlikely a problem with burning then. If it is such an issue it is probably the drive itself then.  But it could be many other things too - like an issue with the hard drive.  Hopefully someone else will come along with some more suggestions...

I know on the main page Ubuntu will send out a CD free for you as well if you wish to try that.

---

### Post by Drakkor on 2006-11-02
The first thing you should check is the md5sums on the downloaded file,to make sure the downloaded .iso file is not corrupt. Depending on which one you downloaded,here are the sums that should match:

b9a5be3a5858ade278d664d41310a4ab  ubuntu-6.06.1-alternate-amd64.iso
6cb8582aa5615ed4616165743a0868d7  ubuntu-6.06.1-alternate-i386.iso
0b5b3df02da3d9ed6f4ac482cf541f04  ubuntu-6.06.1-alternate-powerpc.iso
50e3912c555f98f7bca56b2a0200b205  ubuntu-6.06.1-desktop-amd64.iso
fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
502911770ad173dbe82c698379ed7d11  ubuntu-6.06.1-desktop-powerpc.iso
8254b0f3696ed17c52a2cb59c9ebd2cc  ubuntu-6.06.1-server-amd64.iso
5ad76d8b380ab5be713e5daa9ea84475  ubuntu-6.06.1-server-i386.iso
6d1c3b5cb41661365b3db5cf12bb2836  ubuntu-6.06.1-server-powerpc.iso
2ccc1ec608040e6aac8913a016c31bed  ubuntu-6.06.1-server-sparc.iso

If those are ok, as stated burn on a CD-R at a minimum speed,so as to not make any errors, then when you boot, select the second option to "Check CD for defects", if no checksums fail,it should boot to the live CD ! Good luck ! :)

---

### Post by leavingOS2 on 2006-11-04
Still haven't been able to live boot before my first install.  However:

The md4sum checks out OK.

I took the CD to another machine I have, Celeron 950 w/256MG with DVD player with win2k.  It passes the "Check CD for errors" check.  I tried live booting from this machine.  It gets way past the stopping point on my target machine, however it does get stuck before actually giving me a live boot.  I suspect it is the ATI Raedon 7000 64MG PCI video card in this machine.  I did try setting VGA to 640x480x16 before attempting live boot, but still eventually freezes on a blinking cursor.

Back to my main machine.  I'm going to try updating the CDR unit with something modern and see how that goes.

---

### Post by oldgeek on 2006-11-04
For what it's worth I have had two install failures with similar symptoms to yours and it was on two different systems/motherboards.  The same LiveCD did however work just fine on two other systems that I have here.  I posted the info at launch pad because I am convinced it is an issue with some chip sets.

My suggestion would be to try a different distro to verify that it is a hardware compatibility issue.  SUSE is imo the best out there for handling hardware issues but you'll need to dl and burn 5 cd's to test out.  I've tried several other liveCD's from other distros and it's a real crap shout.

Good luck.  Ubuntu is a great system if you can get it working.

---

### Post by leavingOS2 on 2006-11-04
I'm posting this from my first live boot!!!!

Thanks to all for suggestions and feedback.

If it's helpful to anyone else, what seems to have made the difference is switching out the CDR-(2X writer) for a CD-ROM (8x reader).

Now its on to learning my way around Linux, so I can get it installed.  I'm still mulling partitioning and keeping some legacy stuff.  I have an OS/2 partition which runs a Win3.1 checkbook program that I'd like not to give up.  I have a Win98 partition that runs my Umax Astra 220S scanner which I'd keep until I get it working under Ubuntu.  I have a WinXP partition that doesn't run well do to installation screw up, but I may need to keep in order to run an occasional Win program, or to install programs that won't install under Wine.  I have Win 2K which I may install in place of Win XP.  I have IBMs Boot Manager with LVM which I may use until I can learn my way around Linux' boot managers.

Thanks again to all

---

### Post by Drakkor on 2006-11-04
Great ! :p  Welcome to Ubuntu, I love it !!

---

