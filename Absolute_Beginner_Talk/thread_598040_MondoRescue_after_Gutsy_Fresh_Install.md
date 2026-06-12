---
title: "MondoRescue after Gutsy Fresh Install"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by ityro on 2007-10-31
I did a fresh install of Gutsy and tried MondoArchive again (Mondo has not worked for me since Dapper).  It failed but the error message is different and I have decided this a good sign.  I made several tries but all failed.  When I insert CD#1 it boots and looks good but: 

All attempts got the same error message:
"Could not mount devices /dev/sda1  dev/hda1  /dev/hda1_dup  /dev/hda2_dup
shall I abort?".  If I choose to continue it verifies the tar balls but eventually displays lotsa red stuff and I abort.

sda1 is backups for XP on the external HDD.  hda1 is XP on the internal HDD.  hda2 is Gutsy on the internal HDD but I don't know what the "dup" means.  I do not select any XP for backup, only Gutsy.

I used no excludes and the external HDD was connected and online.  All file systems are set to mount at boot time.  If anyone has an idea for getting around the problem I will give it a try, would really like to have my Mondo back.

THANKS FOR YOUR TIME.

MY SYSTEM:
Dual-boot XP/Ubuntu 7.10 on a HP/Compaq nx9010 notebook w/40GB HDD.  Iomega 80GB usb external HDD.  ATI Display: PCI Bridge [GP 340M]  Radeon IGP 330M/340M/350M RS200/RS200M  AGP Bridge [IGP 340M].

---

### Post by ruibernardo on 2007-10-31
Mondorescue had some [problems in Feisty with UUIDs]("http://ubuntuforums.org/showthread.php?t=430866"). Didn't tried it in Gutsy, but apparently they were [fixed]("http://changelogs.ubuntu.com/changelogs/pool/universe/m/mondo/mondo_2.22-1/changelog").

---

### Post by ityro on 2007-10-31
Thanks for info I do appreciate your reply.

Umbert

---

### Post by ruibernardo on 2007-10-31
Maybe you could try the deb packages from mondorescue for gutsy (not tested): [ftp://ftp.mondorescue.org/ubuntu/7.10](ftp://ftp.mondorescue.org/ubuntu/7.10).

---

### Post by ityro on 2007-10-31
I probably should play with it but from previous (many) searches on these forums since Feisty, I was led to believe the problem was definitely with Ununtu not Mondo.  I was hoping Mondo would be considered more important than eye candy but I guess Mondo didn't make the cut this time. Wait 'til next year!

Thanks again for your interest, I really appreciate your efforts. . .

---

### Post by ityro on 2007-11-02
I played with the deb files available on the MondoRescue site with the Package Manager files plus a mixture of both. Nothing worked for me.

Versions were interesting:

Mindi version on the MondoRescue site was  1.2.5 while PkgMgr has 2.22-1
Mindi-busybox on the MondoRescue site was 1.2.2-4 while PkgMgr has 1.2.1-2
Mondo version on the MondoRescue site was 2.2.5 while PkgMgr has 2.22-1

The PkgMgr advised I was downgrading not upgrading and the Update Manager jumped on my bones to correct my foolishness.  Bottom line: my attempts to run Mondo failed again.
      
MY SYSTEM:
Dual-boot XP/Ubuntu 7.10 on a HP/Compaq nx9010 notebook w/40GB HDD.  Iomega 80GB usb external HDD.  ATI Display: PCI Bridge [GP 340M]  Radeon IGP 330M/340M/350M RS200/RS200M  AGP Bridge [IGP 340M].

---

### Post by ruibernardo on 2007-11-03
Ityro, 

try to pin the packages, so they don't get downgraded. Edit or create /etc/apt/preferences and put/add this in it:
```
Package: mindi
Pin: version 2.23*
Pin-Priority: 500

Package: mondo
Pin: version 2.23*
Pin-Priority: 500
```If mindi-busybox is also being downgraded (wasn't happening to me), add an entry on the /etc/preferences file for it too. That worked for me [some time ago]("http://ubuntuforums.org/showpost.php?p=2663837&postcount=5").

---

### Post by ityro on 2007-11-03
epimeteo,
Thanks for the How To. My problem was not getting downgraded but upgraded because the Pkg Mgr had newer versions of Mindi and Mondo.  Also, I found no version 2.23 only the packages listed on my last post.

---

### Post by ityro on 2007-11-03
Epimeteo,
I answered your last post don't know where it went. The e-mails sent by the forums are now going to the Spam Folder. Oh well!

Thanks for the howto. My problem was getting upgraded not downgraded as the Pkg Mgr had newer versions than Mondo site. I saw no version 2.23*. Thanks again.

---

### Post by ruibernardo on 2007-11-03
EDIT: I've wrote this and didn't see your last post. Glad it worked for you too.

Sorry, I haven't explained what the file /etc/apt/preferences does and how it works. This file (from "man apt_preferences") "can be used to control which versions of packages will be selected for installation."

The "Package:" is obvious...

"Pin: version 2.23*" and "Pin-Priority: 500" (from the man page) "causes a version to be installed unless... the installed version is more recent".

When you «block» a package version on Synaptic, you are editing /etc/apt/preferences almost like this, but Synaptic will not allow an upgrade until you «unblock» the package. Here 500 will allow it if a version 2.23* appears (lets hope that 2.23 will have this bugs corrected).

You can see that the version number of mindi (from the mondo website) is different than the one on the repositories. 
> **ityro said:**
> 
Mindi version on the MondoRescue site was  [COLOR=Blue]**1.2.5**[/COLOR] while PkgMgr has **[COLOR=Red]2.22-1[/COLOR]**
Mindi-busybox on the MondoRescue site was [COLOR=Blue]**1.2.2-4**[/COLOR] while PkgMgr has [COLOR=Red]**1.2.1-2**[/COLOR]
Mondo version on the MondoRescue site was **[COLOR=Blue]2.2.5[/COLOR]** while PkgMgr has [COLOR=Red]**2.22-1**[/COLOR]

I don't know why this is that way, but APT is downgrading the packages because the packages we downloaded from the website have an inferior value than the ones on the repos (2.2.x < 2.22). mindi-busybox appears to be the only package that has a good version number on the website and on the repositories.

So, with the pin on /etc/apt/preferences, these packages will only be upgraded if a version 2.23* appears on the repositories, and that avoids the downgrading until a new (corrected) version appears on the repositories. If you really don't want to use the /etc/apt/preferences, try blocking the packages in Synaptic. It's more simple.

I hope that was not very confusing, but that worked for me, and if you did get the website packages working without problems, this will prevent them from being "downgraded".

---

### Post by ityro on 2007-11-03
epimeteo,

I can't thank you enough for your time and effort. You cleared up many issues and now it's up to me.  Tomorrow I will put everything back the way I found it, make a plan of actions based on your info, and then just do it. 

THANKS AGAIN.

---

### Post by ityro on 2007-11-03
eptmeteo,
I see that my last "Quick Reply" did not make it to the Forum. No matter, I got a totally diferent error message but the same result, It failed. Something different on my system.  The error message this time was : " Kernal panic - not syncing: VFS: unable to mount root fs on unknown - block(1,0)"  and the "A" light (upper case) flashes but nothing happens.

I had no Preferences file so I created one (see ScreenShot) but probably did not get it right because the Update Manager jumped me again.  But, while I was looking around the Package Manager I found the option to "Lock the Version" so I tried it. This time the Update Manager was silent so I manually launched the Update manager and it still remained silent. Small victory.

I would like to thank you for all your help I really did learn a lot.  And now it's opening time in the P.I. and time for a tall glass of Irish.

THANKS AGAIN for your knowledge and patience.
        
MY SYSTEM:
Dual-boot XP/Ubuntu 7.10 on a HP/Compaq nx9010 notebook w/40GB HDD.  Iomega 80GB usb external HDD.  ATI Display: PCI Bridge [GP 340M]  Radeon IGP 330M/340M/350M RS200/RS200M  AGP Bridge [IGP 340M].

---

### Post by ityro on 2007-11-03
eptmeteo,

I sent this yesterday but I don't see it on the Forum so here it is again:

I see that my last "Quick Reply" did not make it to the Forum. No matter, I got a totally diferent error message but the same result, It failed. Something different on my system.  The error message this time was : " Kernal panic - not syncing: VFS: unable to mount root fs on unknown - block(1,0)"  and the "A" light (upper case) flashes but nothing happens.

I had no Preferences file so I created one (see ScreenShot) but probably did not get it right because the Update Manager jumped me again.  But, while I was looking around the Package Manager I found the option to "Lock the Version" so I tried it. This time the Update Manager was silent so I manually launched the Update manager and it still remained silent. Small victory.

I would like to thank you for all your help I really did learn a lot.  And now it's opening time in the P.I. and time for a tall glass of Irish.

THANKS AGAIN for your knowledge and patience.
        
MY SYSTEM:
Dual-boot XP/Ubuntu 7.10 on a HP/Compaq nx9010 notebook w/40GB HDD.  Iomega 80GB usb external HDD.  ATI Display: PCI Bridge [GP 340M]  Radeon IGP 330M/340M/350M RS200/RS200M  AGP Bridge [IGP 340M].

---

### Post by ruibernardo on 2007-11-03
I'm trying myself in a Gutsy VM in QEMU (still running Feisty here). Aparently it's working. 

I've downloaded the packages from [ftp://ftp.mondorescue.org/ubuntu/7.10](ftp://ftp.mondorescue.org/ubuntu/7.10), installed them (some "sudo apt-get install -f" to resolve some dependencies) and then I've pin them in /etc/apt/preferences (from what you say I guess that «locking» them in Synaptic will do too).

I'm running mondoarchive now. I had to rename the swap partition by  removing the UUID and renaming it /dev/sda5 in /etc/fstab so I could run it and it seems it's working fine for now.

If I find more issues when I'll try to restore, I'll post them.

---

### Post by ityro on 2007-11-04
I used same path with two exceptions:
1. I used "locked" in Pkg Mgr.
2. Did not change fstab where my Swap is /dev/hda5 and is the only reference to Swap; however Swap also is shown as /dev/hda3 as "extended" when I ran fdisk -l

Best of luck on your test run. I suspect something is not right in my system (or me).

---

### Post by ruibernardo on 2007-11-04
> **ityro said:**
> Kernal panic - not syncing: VFS: unable to mount root fs on unknown - block(1,0)"  and the "A" light (upper case) flashes but nothing happens.

While backing up the VM, I was reading the [mondorescue FAQ]("http://trac.mondorescue.org/wiki/FAQ") and I've crossed by "Q26/ Why is my kernel doing a panic at restore time, when it works perfectly at archive time ?". It seems to be your case.

It talks about an option for VFS in mindi, so maybe that's your problem. You should try it (unfortunately you will need to backup one more time).

Good luck.

---

### Post by ityro on 2007-11-04
epimeteo,

Thanks for the new info.  I have already installed the patch you found but before I did I launched Mindi. Don't know why I did that. Mindi did not like something that reminded me of a problem after installing Feisty and sure enough the problem came back with the fresh install of Gutsy, a system loop. So I also installed that patch.

I will now do a fsck, backups and then MONDO!  It will be awhile but I shall return. Hopefully with good news.

---

### Post by ityro on 2007-11-04
epimeteo,

It blew up instantly. See attached ScreenShot.

I will now take a food break. Then I will uninstall Mindi and Mondo and install the Package Manager's version and verify the Q&A patch is still installed. Then I will try it again.

---

### Post by ityro on 2007-11-04
epimeteo,

My sincere thanks for all your help but nothing changed the bottom line.  I give up. By the way, the Q&A patch to /usr/sbin/mindi is in the version offered by the Pkg Mgr. I checked my tar backup dated October 28, 2007 and it was already there.

Thanks again, it was fun but after a few months of this I quit. Maybe I should consider a distro where Mondo/Mindi works for everyone.

MY SYSTEM:
Dual-boot XP/Ubuntu 7.10 on a HP/Compaq nx9010 notebook w/40GB HDD and CD-R drive.  Iomega 80GB usb external HDD.  ATI Display: PCI Bridge [GP 340M]  Radeon IGP 330M/340M/350M RS200/RS200M  AGP Bridge [IGP 340M].

---

### Post by ruibernardo on 2007-11-08
ityro, I've being on the mailing list of mondorescue and it's seems that a strange thing is happening here on my Ubuntu Gutsy in both Desktop and Server versions. This isn't/wasn't happening in Feisty and my server was upgraded from Feisty to Gutsy and it is happening on the fresh install of Ubuntu Gutsy also.

From the logfiles of mondorescue and after confirming it in the terminal, it seems that I have differences between the UUID of the swap partition in /etc/fstab and the output of the command "blkid". This could be the cause of the kernel panic.

Could you post here the output of "cat /etc/fstab" and "blkid" just to confirm if it's happening to you too?

Thanks

EDIT: forget it, it is a mondoarchive issue, not a mondorestore issue, so it isn't your case, thank you anyway.

---

### Post by stepheny on 2007-11-13
Shouldn't someone who has a grasp of what is wrong with the version in the reository report the bug in [https://launchpad.net/ubuntu/+source/mondo/+bugs](https://launchpad.net/ubuntu/+source/mondo/+bugs) ?

---

### Post by ruibernardo on 2007-11-13
I think it's an upstream problem(?) - don't even know if it's really a bug. Debian also has this crazy versions numbers. 

As you can see [here]("http://packages.debian.org/changelogs/pool/main/m/mondo/mondo_2.24-2/changelog"), the debian maintainer of mondorescue has changed the versions numbers to 2.03.1-1 back in 2004. I guess it should have been 2.0.3.1-1 but it was released has 2.03.* in debian. Don't know why it was decided that way, though. I don't believe that Ubuntu maintainer will change that.

---

### Post by stepheny on 2007-11-13
I just would like to protect others from my experience. I have used Mondo for years and trusted it to restore my system because I had done just that many times. I carried on making backups and comparing them and because the compare said the backups were ok I believed they were.

But when I finally needed to restore my system it didn't work!

---

### Post by ityro on 2007-11-22
epimeteo,

Sorry for the delay in my response but when it rains it pours. My PC broke, turns out it's the keyboard and HP Manila says 12 to 15 weeks to get a replacement. Unbelievable.  So, I now have an external keyboard and  mouse but it's a tacky setup and some problems from built-in keyboard continue, like typing this post.

I do not know how to post a multi-screen list so I will send two screenshots for fstab and one for blkid. Next I will learn how to post long lists.

Thanks again and hope this info will help.

---

### Post by ityro on 2007-11-22
epimeteo,

I got it.  Thanks again.



bob@bob-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc           proc         defaults                      0  0  
# Entry for /dev/hda2 :
UUID=51881bb5-ab91-4c7b-92ce-ea3aadf824d7  /               ext3         defaults,errors=remount-ro    0  1  
# Entry for /dev/hda1 :
UUID=FC48C78B48C742DE                      /media/hda1     ntfs-3g      defaults,locale=en_PH.UTF-8   0  1  
# Entry for /dev/hda5 :
UUID=b3772b3d-43ff-451e-86c5-e4361b17cf58  none            swap         sw                            0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto,exec              0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec           0  0  
/dev/hda1                                  /media/hda1     ntfs-3g      defaults,locale=en_PH.UTF-8   0  0  
/dev/hda5                                  /media/hda5     swap         defaults                      0  0  
/dev/sda1                                  /media/Iomega   ntfs-3g      user                          0  0  
/dev/sda2                                  /media/usbdisk  ext3         errors=remount-ro,users,user  0  0  
/dev/hda2                                  /media/hda2     ext3         defaults                      0  0



I thinkl.

---

