---
title: "I did a dumb, dumb, thing!"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by keith40228 on 2008-02-03
I was excited.  I received my cd in the mail.  Installed same.  Can't reboot into XP.  Assumed there would be uninstall provision.  Can't find it, if it exists.  

Dell Inspiron 1000 laptop.  How do I get out of this and start over?  

Would greatly appreciate any help.  byt I don't have a recovery cd.  have ordered them form dell.

Is there a Louisville Metro user group that meets somewhere?

Thanks!

---

### Post by r4ik on 2008-02-03
Try,

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Good luck !

---

### Post by hardyn on 2008-02-03
depending on how quicky you fired through the partitions sections of the install, you could be in for a really big headache; please post your partitioning options

---

### Post by TheBoat on 2008-02-03
It sounds like you just quickly installed Linux over Windows.  To keep two operating systems available you will need to set up a dual-boot, which requires multiple partitions for your different OSs. Here is a website I recommend on dual-booting.

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

If you did install Linux on your Windows partition, then you probably can not get back your original configuration.  There is no way to uninstall an OS.

-TheBoat

---

### Post by Malta paul on 2008-02-03
Hi, There is a LoCo Group in Kentucky: 

United States / Kentucky
EricLake
KentuckyTeam
#ubuntu-kentucky
[MAILTO] [email]ubuntu-us-ky@lists.ubuntu.com[/email]
[WWW] [http://ubuntu-ky.ubuntuforums.org](http://ubuntu-ky.ubuntuforums.org) 

For a list of LoCo'   ,[https://wiki.ubuntu.com/LoCoTeamList](https://wiki.ubuntu.com/LoCoTeamList)

Regards your problem you might like to check out:[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Hove fun:)

---

### Post by motion parallax on 2008-02-03
Hasn't seemed like the Kentucky group is very active lately.  Then again I've only been an Ubuntu user for a week :D

Welcome to Ubuntu!  How do you like Louisville?

---

### Post by keith40228 on 2008-02-04
> **motion parallax said:**
> Hasn't seemed like the Kentucky group is very active lately.  Then again I've only been an Ubuntu user for a week :D

Welcome to Ubuntu!  How do you like Louisville?

Well... I've lived in louisville/Jefferson County literally since conception so I guess I don't have any reference point.  I haven't had any desire to live anywhere except Pensacola.

---

### Post by keith40228 on 2008-02-04
> **hardyn said:**
> depending on how quicky you fired through the partitions sections of the install, you could be in for a really big headache; please post your partitioning options

I'm so new and ignorant, I don't know my partition options.  At present I'm just waiting for my recovery disks so that hopefully I can reinstall **X**tra**P**utrid  Also I've requested 2 Ubuntu books form the library.

---

### Post by jordanmthomas on 2008-02-04
OK, what does this output (from a terminal:  applications -- accessories -- terminal)
```
sudo fdisk -l
```
This will list all the partitions on all your discs.  From here we can see if XP is still hanging around or if you've accidentally formatted it.

---

### Post by keith40228 on 2008-02-04
> **r4ik said:**
> Try,

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Good luck !
Thanks!

---

### Post by keith40228 on 2008-02-04
> **hardyn said:**
> depending on how quicky you fired through the partitions sections of the install, you could be in for a really big headache; please post your partitioning options

Used Partition Manager and came up with:
   /dev/sda - GParted

Partition        Filesystem       Size              Used        Unused        Flags
/dev/sda1     ext3                36.01 GiB     2.55 GiB   33.46 GiB     boot
/dev/sda2     extended          1.25 GiB     
/dev/sda5     linux-swap         1.25 GiB

---

### Post by keith40228 on 2008-02-04
> **jordanmthomas said:**
> OK, what does this output (from a terminal:  applications -- accessories -- terminal)
```
sudo fdisk -l
```
This will list all the partitions on all your discs.  From here we can see if XP is still hanging around or if you've accidentally formatted it.

output from sudo fdisk -l

/dev/sda1   *  1   4701   37760751      83   linux
/dev/sda2            4702     1309297+     5  extended
/dev/sda5            4702     1309266       82 linux swap / solaris

---

### Post by NilsHG on 2008-02-04
looks like you were a bit too hasty. from what i can tell these are all linux partitions. i am afraid your windows is gone.

*edit* whats with sda 3 and 4? why is swap 5 already? there might be hope yet.*/edit*

---

### Post by legend2440 on 2008-02-04
Sorry to say it looks like the Ubuntu CD partitioned and formatted your drive
XP is gone until you get the recovery disks

---

### Post by NilsHG on 2008-02-04
> **legend2440 said:**
> Sorry to say it looks like the Ubuntu CD partitioned and formatted your drive
XP is gone until you get the recovery disks

dont blame the cd :(

---

### Post by jordanmthomas on 2008-02-04
> **NilsHG said:**
>  whats with sda 3 and 4? why is swap 5 already? there might be hope yet.

It's because of extended partitions.  Since you can have 4 primary, sda5 is the first logical partition you can have.  (I think)

---

### Post by hyper_ch on 2008-02-04
> **jordanmthomas said:**
> It's because of extended partitions.  Since you can have 4 primary, sda5 is the first logical partition you can have.  (I think)

Good thinking :) however bad for the TO!

---

### Post by aimhigher101 on 2008-02-04
if ur trying to get rid of the windows os just use a low lvl format on ur hard drive (will wipe everything of it So save all thats needed). That should make that hard drive empty with no os. Then you can boot from disk and install linex and then $$ ur on (hopefully)

---

### Post by keith40228 on 2008-02-04
THANKS! to everyone.  This has definitely been a learning experience.  The links mentioned have turned up some gold nuggets.  I'll play with Ubuntu until I can reload XtraPutrid and then set up dual boot.

Thanks again!

P.S.
If you want somewhere to meet, let me know.  I'll get with my church, Bethlehem Baptist and see about meeting space.  Only problem would be net access.  No wifi.

---

### Post by motion parallax on 2008-02-04
> **keith40228 said:**
> Well... I've lived in louisville/Jefferson County literally since conception so I guess I don't have any reference point.  I haven't had any desire to live anywhere except Pensacola.

Been in this area most of my life, so I understand.  

If they ever get the Kentucky Ubuntu meetings going, let me know.

---

