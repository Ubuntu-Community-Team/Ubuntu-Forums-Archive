---
title: "Erase CD-RWs"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2006-05-24
Can u erase cd-rws in GNOME????

---

### Post by nanotube on 2006-05-24
hmm, i know you can if you install "gnomebaker". don't know about regular gnome cd writer though...

---

### Post by youthforlinux on 2006-05-24
okay can i use *apt-get* to get that??!!

---

### Post by nanotube on 2006-05-24
[QUOTE=youthforlinux]okay can i use *apt-get* to get that??!![/QUOTE]
yes you can! :)
```
sudo apt-get install gnomebaker
```

---

### Post by Klaidas on 2006-05-24
Sure you can erase them :)
They're RW, and you're using one of the best linux systems out there ;)

---

### Post by youthforlinux on 2006-05-24
awesome!!!!

---

### Post by wpshooter on 2006-05-24
[QUOTE=youthforlinux]awesome!!!![/QUOTE]

Youthforlinux:

Your question about erasing CD-RWs was one of the first things I had to figure out when I started looking at Ubuntu a few weeks ago.

Let me save you some of the time I spent looking for a solution.

If you are not already using it, start using the dapper drake beta until it becomes released (hopefully shortly).  And once you have it installed go to the add/remove applications section and add the program called K3b.  And then probably should reboot and then see if the system finds any available updates for the K3b program you just installed.

Once you have done the above give the K3b program a try.  IMO, it is a far better program than any of the other CD writer type programs (including the Gnomebaker program mentioned in prior posts) and it handles erasing CD-RW and makes writing to them a fairly simple process.  One thing I particularly like is the flag that you can turn on (which is NOT on by default) to do a verification of the copy process after the copy is completed.  Please note that I found that there was a bug in the unpatched version of K3b that I tried earlier on in this entire process that made the program fail if I attempted to use the verification part of the process.

Good luck.

---

### Post by youthforlinux on 2006-05-24
for some reason k3b is having a problem erasing my cd-rws

---

### Post by wpshooter on 2006-05-24
[QUOTE=youthforlinux]for some reason k3b is having a problem erasing my cd-rws[/QUOTE]

Are you using Dapper Drake or Breezy Bader ?

I had the problems when I was using Breezy.  Going to Dapper and installing the updates has cured the ills for me.

---

### Post by user1397 on 2006-05-24
[quote=wpshooter]Are you using Dapper Drake or Breezy Bader ?

I had the problems when I was using Breezy.  Going to Dapper and installing the updates has cured the ills for me.[/quote]
yes but dapper beta is still in development and not 100% stable, especially to a beginner.  just wait 8 more days to get the stable release of dapper

---

### Post by wpshooter on 2006-05-24
May still be in development, but IMO, it is better than using older Breezy.  I don't think there is any such thing as 100% stable software (not even if you or I wrote it).  Unless poster has some misssion critical apps, then get the latest version of Dapper beta and play around with it a bit to get the feel and then get the release version when it comes out.

---

### Post by user1397 on 2006-05-24
[quote=wpshooter]May still be in development, but IMO, it is better than using older Breezy.  I don't think there is any such thing as 100% stable software (not even if you or I wrote it).  Unless poster has some misssion critical apps, then get the latest version of Dapper beta and play around with it a bit to get the feel and then get the release version when it comes out.[/quote]
But always warn him or her to backup data first, as there are no guarantees regarding betas.

---

### Post by wpshooter on 2006-05-24
[QUOTE=erik1397]But always warn him or her to backup data first, as there are no guarantees regarding betas.[/QUOTE]

Yes, you are correct.  But there is a clear warning on here to not to use on production machine.  I think all testing on this O/S, should really be done on a spare machine, for now.

---

### Post by youthforlinux on 2006-05-25
[QUOTE=wpshooter]Are you using Dapper Drake or Breezy Bader ?

I had the problems when I was using Breezy.  Going to Dapper and installing the updates has cured the ills for me.[/QUOTE]

It seemed that the problem only happened on the computer that had Breezy.

---

### Post by Frank Golden on 2006-05-25
[QUOTE=wpshooter]Youthforlinux:

Your question about erasing CD-RWs was one of the first things I had to figure out when I started looking at Ubuntu a few weeks ago.

Let me save you some of the time I spent looking for a solution.

If you are not already using it, start using the dapper drake beta until it becomes released (hopefully shortly).  And once you have it installed go to the add/remove applications section and add the program called K3b.  And then probably should reboot and then see if the system finds any available updates for the K3b program you just installed.

Once you have done the above give the K3b program a try.  IMO, it is a far better program than any of the other CD writer type programs (including the Gnomebaker program mentioned in prior posts) and it handles erasing CD-RW and makes writing to them a fairly simple process.  One thing I particularly like is the flag that you can turn on (which is NOT on by default) to do a verification of the copy process after the copy is completed.  Please note that I found that there was a bug in the unpatched version of K3b that I tried earlier on in this entire process that made the program fail if I attempted to use the verification part of the process.

Good luck.[/QUOTE]

Hi All,
   Just attempted to erase CD-RW using K3b failed until I changed ownership and permissions of my CD/DVD drive.?

Below is output of error message.

System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-23-686
Devices
-----------------------
MATSHITA DVD-RAM UJ-845S D201 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=10 -tao driveropts=burnfree -eject blank=fast -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-23-686

/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
/usr/bin/X11/cdrecord: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM

Using Latest Dapper, fully updated.
On Acer Aspire 5672WLMi notebook, Centrino Duo (T2300@1.66GHz), 2GB DDR2 PC5300 ram, ATi Radeon
x1400 video with 128MB dedicated VRAM/384 shared, 120GB 5400rpm SATA HDD. 
Dual boot with XP Pro-SP2.

Thanks
Frank Golden

---

### Post by Sef on 2006-05-25
> yes but dapper beta is still in development and not 100% stable, especially to a beginner. just wait 8 more days to get the stable release of dapper

Dapper is not in Beta anymore; it is in RC1 (Release Candidate 1).  

Wikipedia definition:

> Release candidate

The term release candidate refers to a final product, ready to release unless fatal bugs emerge. In this stage, the product features all designed functionalities and no known showstopper class bugs. At this phase the product is usually code complete.

Microsoft Corporation often uses the term release candidate. Other terms include gamma (and occasionally also delta, and perhaps even more Greek letters) for versions that are substantially complete, but still under test, and omega for final testing of versions that are believed to be bug-free, and may go into production at any time. (To many software testers, Gamma testing is an informal phrase that refers derisively to the release of "buggy" or defect-ridden products. It is not a term of art among testers, but rather an example of referential humor.) Gamma, delta, and omega are, respectively, the third, fourth, and last letters of the Greek alphabet. Some users disparagingly refer to release candidates and even final "point oh" releases as "gamma test" software, suggesting that the developer has chosen to use its customers to test software that is not truly ready for general release. Often, beta testers, if privately selected, will be billed for using the release candidate as though it were a finished product.

A release is called code complete when the development team agrees that no entirely new source code will be added to this release. There may still be source code changes to fix defects. There may still be changes to documentation and data files, and to the code for test cases or utilities. New code may be added in a future release.

[Release_Candidate]("http://en.wikipedia.org/wiki/Release_Candidate")

---

### Post by tribaal on 2006-05-30
*bump*

I get the same error in gnomebaker:

Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.

Anybody found a fix for that? The only thing that seems to make my drive burn is to lauch the program with root rights. And I really don't like doing that :(

Thanks a lot!

- trib'

---

### Post by nanotube on 2006-05-30
[QUOTE=tribaal]*bump*

I get the same error in gnomebaker:

Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.

Anybody found a fix for that? The only thing that seems to make my drive burn is to lauch the program with root rights. And I really don't like doing that :(

Thanks a lot!

- trib'[/QUOTE]
hmm, maybe you could try changing your /etc/fstab to mount with read/write, and maybe also to be owned by your user rather than by root. try it, see if it helps.

---

### Post by tribaal on 2006-05-31
Hum well /dev/sg0 doesn't appear in my /etc/fstab, which is pretty strange. Instead, the DVD+-RW appears as /dev/scd0.

As for changing the access rights for /dev/sg0, I tried to change it's ownership, so that it's owned by root and by the "cdrom" group, but I can't seem to do that...
Any idea on how I should do it do that it works?

Here's cat /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           ext3    defaults        0       2
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Changing rights on /dev/sg0:

#> chown root:cdrom sg0
chown: changement de propriétaire pour `sg0': Opération non permise
(Translation: chown: changing owner for 'sg0': Operation not allowed)

I really am not confident with chown (I'm not sure I use it properly)...

Any thouhts?
Thanks a lot!

- trib'

---

### Post by Herman on 2006-05-31
> Can u erase cd-rws in GNOME???? I have never noticed any problems erasing CD-RWs in Gnome (CD/DVD Creator), using Breezy or Dapper.  I always just insert the CD-RW with the old data still on it and I don't even bother worrying about whether it is erased or not. I select the file or files I want to burn to the CD-RW and click 'write to disk'.  Gnome automatically checks first before it starts writing and finds there is already data there. It presents me with a sign > '**Erase information on this disk?**' 'This CD-RW appears to have information already recorded on it.' I am given three choices 'Try Another', Cancel' or Erase Disk'. If I want to erase it, it first erases the old information and then records the new data.
It seems blindingly simple. Is that what you are all trying to do, or have I missed something?
Regards, Herman :D

---

### Post by Egalus on 2006-06-07
I have the same problem, can't get exclusive lock on cd-drive and I already know what is causing this problem, the f..... automount that ubuntu does with empty cd-rw even if this option is disabled in the settings.

I have not found a way to stop the automounting of cd-rws and cause of that am not able to erase them ...

---

### Post by steve.horsley on 2006-06-07
[QUOTE=Egalus]I have the same problem, can't get exclusive lock on cd-drive and I already know what is causing this problem, the f..... automount that ubuntu does with empty cd-rw even if this option is disabled in the settings.

I have not found a way to stop the automounting of cd-rws and cause of that am not able to erase them ...[/QUOTE]
That's fixed in dapper. It automounts, but magically de-mounts (and the icon disappears) when you start writing.

As has been said, with Nautilus you don' t need to erase before writing (in Dapper, I remember problems in the past, Hoary or Breezy), so you only need a separate writer program if you want to erase for some other reason - like another machine needs blanks, or to delete private files.

---

### Post by tribaal on 2006-06-07
Well the what should I reinstal so that it works? I mean I use Dapper, but still cannot have an exclusive lock on my DVD RW drive... 
This is the very last thing that's not working "as it should" for me... I even managed to make the little wifi LED on my Dell to work, it's driving me crazy ;)

In the mean time I run GnomeBaker as root everytime I need to burn something :(

Thanks for the interest though :)

- trib'

---

### Post by kb2wdi on 2006-06-15
I had this issue in NeroLinux and cdrecord as well. First I added the line;

KERNEL=="sg0", GROUP="cdrom"

to "/etc/udev/rules.d/40-permissions.rules" which fixed the permission, but caused NeroLinux to lockup. The device "/dev/sg0" did not exist for me in breezy, and I do not use ide-scsi (although I do have a SCSI HD). My final solution was to just remove it. Comment out the line;

#RUN+="/sbin/modprobe -Qba sg"

in "/etc/udev/rules.d/90-modprobe.rules" and it's gone.

I am able to burn DVD's at 16x again in nero!

---

### Post by odzx on 2007-02-04
is anyone having this problem on edgy?
i have a similar problem with k3b and gnomebaker on edgy 64 bit. i can burn cd and dvd but can only format dvd as root.
i allready added my self to disk group. didnt help. 
any ideas?

---

