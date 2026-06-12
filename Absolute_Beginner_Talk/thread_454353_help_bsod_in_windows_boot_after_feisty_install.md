---
title: "help? bsod in windows boot after feisty install"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by jejunum on 2007-05-25
Installed feisty (alternate cd, ati drivers) and it works fine (no wpa), but now booting into windows gives me a bsod and a reset before I can read any of it!

help!
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       12369    99305797+   7  HPFS/NTFS
/dev/sda3           12370       13585     9767520    c  W95 FAT32 (LBA)
/dev/sda4           13586       14593     8096760    5  Extended
/dev/sda5   *       13586       14544     7703136   83  Linux
/dev/sda6           14545       14593      393561   82  Linux swap / Solaris

I can read my ntfs (windows) partiion fine in ubuntu (& write)

edit: Windows install & ultimate boot cd can not see the windows partition.    have tried safe mode & last good config in windows with no luck.  Any ideas?

edit: im starting to believe the bsod is this "UNMOUNTABLE_BOOT_VOLUME" which appears to be fairly common argh! 
[http://ubuntuforums.org/showthread.php?t=62533](http://ubuntuforums.org/showthread.php?t=62533)
[http://ubuntuforums.org/showthread.php?t=352984](http://ubuntuforums.org/showthread.php?t=352984)

---

### Post by BHelts on 2007-05-25
what version of windows?  download [UBCD]("http://ultimatebootcd.com"), you will need an offline registry viewer.  we will turn off the auto restart function in windows so we can see which BSOD you are getting.

---

### Post by Terl on 2007-05-25
When you say BSOD what are you getting?  XP sometimes will run a blue screen for chkdsk.  Is there an error on the screen?

---

### Post by jejunum on 2007-05-25
> **Terl said:**
> When you say BSOD what are you getting?  XP sometimes will run a blue screen for chkdsk.  Is there an error on the screen?

it just looks like a bsod for the .01 seconds I see it?  an assumption i guess...

> what version of windows? download UBCD, you will need an offline registry viewer. we will turn off the auto restart function in windows so we can see which BSOD you are getting.
version: windows xp pro

great thanks,, downloading then installing.  How does one turn of the auto restart function?

ugh: foolish on my part - had dapper working (sorta) and decided I should try upgrading to feisty.

I was thinking about doing an XP repair (rewriting boot sector?) and then reinstalling grub, but its such a terrible (and possible not going to fix) solution

---

### Post by BHelts on 2007-05-25
i just need to know what version of windows you were using.  that is so i can direct you to the correct registry key.  if you aren't sure we can search the registry it is just slower.

---

### Post by jejunum on 2007-05-25
> **BHelts said:**
> i just need to know what version of windows you were using.  that is so i can direct you to the correct registry key.  if you aren't sure we can search the registry it is just slower.


sure sorry, windows xp professional - sp1? sp2?  not exactly sure any more than that.

---

### Post by Terl on 2007-05-25
> **jejunum said:**
> 

ugh: foolish on my part - had dapper working (sorta) and decided I should try upgrading to feisty.

I was thinking about doing an XP repair (rewriting boot sector?) and then reinstalling grub, but its such a terrible (and possible not going to fix) solution

If you want to get to feisty from dapper the fastest way is do download feisty and reinstall.  There is no way to upgrade direct from dapper to feisty.  You'd have to upgrade to edgy first.  It is much cleaner to reintstall.

---

### Post by jejunum on 2007-05-25
> **Terl said:**
> If you want to get to feisty from dapper the fastest way is do download feisty and reinstall.  There is no way to upgrade direct from dapper to feisty.  You'd have to upgrade to edgy first.  It is much cleaner to reintstall.

yes, thats what I learnt (after messing aroudn with it alot) and now I cant get into windows...and still no WPA working for me.  All in all a giant stupidity on my part.   (because ATI drivers are a mess, and that was a waste of time, until it was shown how to do it for idiots like myself)

Still downloading ubcd

---

### Post by Terl on 2007-05-25
I think BHelts can help you get back into windows okay.

I have reinstalled Ubuntu a couple times because I messed it up.  Heck, I think we all do when we first start :)

---

### Post by BHelts on 2007-05-25
ok.  once you have UBCD burned, boot into it and load 'Offline NT Password & Registry Editor'.  you will want to load the registry from c:\windows\system32\config.  navigate to HKLM\SYSTEM\CurrentControlSet\Control\CrashControl and in the right hand pane right click on "AutoReboot" and click on "Modify."  In the resulting dialog box, change Value Data from 1 to 0.  This will freeze windows on the blue screen and you will be able to then gather more information on which BSOD it is.  let me know if you have any questions.

---

### Post by BHelts on 2007-05-25
sorry.... HKLM means HKEY_LOCAL_MACHINE.  You may have known that, just trying to clarify.

---

### Post by jejunum on 2007-05-25
> **BHelts said:**
> sorry.... HKLM means HKEY_LOCAL_MACHINE.  You may have known that, just trying to clarify.

thanks.  was unable to get the pw & regedit to work, no harddrives found - couldnt get any of the drivers (?) to recognize harddrive.

any ways to edit registry from linux?  as I can see my ntfs partition...

---

### Post by Happy_Man on 2007-05-25
Hmm... I'm not sure... I know you can open registry files from Ubuntu using Gedit, but I'm not sure whether they will save correctly. Perhaps someone else knows? :confused:

---

### Post by BHelts on 2007-05-25
i'm not sure to be honest if there is a remote registry viewer for windows in linux, i kind of doubt it.  can you boot into windows in safe mode without it blue screening?

---

### Post by jejunum on 2007-05-25
> **BHelts said:**
> i'm not sure to be honest if there is a remote registry viewer for windows in linux, i kind of doubt it.  can you boot into windows in safe mode without it blue screening?

nope unable to boot into safe mode either.

---

### Post by BHelts on 2007-05-25
ok, browse your windows directory in ubuntu in two windows.  in the first window navigate to windows\system32\config and in the second window navigate to "System Volume Information"\restore

in the restore folder there should be a bunch of folders the look something like {b43225dg.....}, sort by date, and lets look at the newest 5 or 6.

in those folders there should be files that have names like regbksystem and regbksam

let me know how that goes so far.

---

### Post by jejunum on 2007-05-25
> **BHelts said:**
> ok, browse your windows directory in ubuntu in two windows.  in the first window navigate to windows\system32\config and in the second window navigate to "System Volume Information"\restore

in the restore folder there should be a bunch of folders the look something like {b43225dg.....}, sort by date, and lets look at the newest 5 or 6.

in those folders there should be files that have names like regbksystem and regbksam

let me know how that goes so far.

in my System Volume Information folder i have 1 folder  (_restore{5D63037D-2B87-4BB7-A7F3-6C8D53AF01DF}) and 2 files (MountPointManagerRemoteDatabase & tracking.log)

---

### Post by BHelts on 2007-05-25
ok open the restore folder and tell me what's in there.

we are going to perform a manual registry restore through linux.....  this is fun.

---

### Post by jejunum on 2007-05-25
52 folders, RP148--> RP199 (friday may 25, 07 newest)

files _driver.cfg, drivetable.txt, fifo.log, _filelsts.cfg

Dont suppose theres any easier way to get ultimate boot cd to work on my latpop (didnt mention hardware - oops, its a e1505)

edit: why are we restoring the registry, i thought the objective was to stop the rest so we can figure out what the BSOD is saying?

---

### Post by BHelts on 2007-05-25
ok, we are almost done.

open rp197 or rp198 and tell me what's in there.

also, in windows\system32\config rename system to system.old

---

### Post by jejunum on 2007-05-25
RP197: 637 files




RP198: 81 files
directory named snapshot: has files in it like _registry_machine_sam
dll files ( like A0034286.dll
ini files
pnfs 
inf files
exe
log 
drivetable.txt

what exactly shoudl I be looking for?

---

### Post by BHelts on 2007-05-25
ok.  in rp197 open the snapshop folder, in the snapshot folder copy _registry_machine_system and paste it into the windows\system32\config folder, when it is in that folder, rename it to system, remember to rename the old system to system.old first, then go ahead and try to boot windows.  do the same with _registry_machine_sam, _registry_machine_default, and _registry_machine_security.  In windows\system32\config rename sam to sam.old, default to default.old and so on, then rename the _registry_machine_***** to just *****.  when you are done you should have in windows\system32\config:  system.old and system, sam.old and sam, default.old and default, and security.old and security.  when that is done, try booting into windows.  this will tell us whether the blue screen was software (registry) related or hardware related.  let me know

---

### Post by jejunum on 2007-05-25
> **BHelts said:**
> ok.  in rp197 open the snapshop folder, in the snapshot folder copy _registry_machine_system and paste it into the windows\system32\config folder, when it is in that folder, rename it to system, remember to rename the old system to system.old first, then go ahead and try to boot windows.  do the same with _registry_machine_sam, _registry_machine_default, and _registry_machine_security.  In windows\system32\config rename sam to sam.old, default to default.old and so on, then rename the _registry_machine_***** to just *****.  when you are done you should have in windows\system32\config:  system.old and system, sam.old and sam, default.old and default, and security.old and security.  when that is done, try booting into windows.  this will tell us whether the blue screen was software (registry) related or hardware related.  let me know

sorry to be such a moron, but how?  i can see all these files but cant edit them...How does one edit NTFS files?

---

### Post by BHelts on 2007-05-25
i don't think that makes you a moron.  i do not know the answer to that.  and i do not have any ntfs partitions on my ubuntu box.  i will find out, i believe by default ntfs folders are read only, but how to make them read/write i'm not sure.  i'll get back to you shortly.

---

### Post by BHelts on 2007-05-25
[check out this link]("http://ubuntuforums.org/showthread.php?t=453500&highlight=ntfs+read+only%3F")

and maybe install the ntfs-3g config mentioned in one of the posts.  then mount your windows partition as read write?

---

### Post by jejunum on 2007-05-25
i installed ntfs-config but the only option is enable write support for external device, internal is grayed out.

grrr

---

### Post by BHelts on 2007-05-25
how about if you unmount the windows partition first?  sorry, i'm flying by the seat of my pants now, i'm honestly not sure about how to go about this.

---

### Post by jejunum on 2007-05-25
new piece of information, tried to boot in with windows cd to overwrite mbr.

cant read drive (when at the partiotioning screen)

fixmbr does nothing
maybe the reason ubcd couldnt see it is mbr is some how corrupt. or something something?

reset: used ntfs-config, managed to mount it as C: with apparent read acess.

should i do above steps now?

---

### Post by BHelts on 2007-05-25
yes, give those steps a try, then see if you can get windows to boot using the normal grub menu.

---

### Post by jejunum on 2007-05-25
system --> system.old & replace with snapshot/_REGISTRY_MACHINE_SYSTEM

sam --> REGISTRY_MACHINE_SAM

default -->REGISTRY_USER_.DEFAULT

security -->REGISTRY_MACHINE_SECURITY.LOG

software -->REGISTRY_MACHINE_SOFTWARE

ok resetting...

---

### Post by jejunum on 2007-05-25
same thing.  reset after bsod

---

### Post by BHelts on 2007-05-25
did you rename the _registry_machine_***** to *****?
SECURITY.LOG will not work, if there is no SECURITY, rename the SECURITY.old in windows\system32\config back to SECURITY

---

### Post by BHelts on 2007-05-25
you can also have a look at:
[info on registry tool in UBCD]("http://home.eunet.no/~pnordahl/ntpasswd/bootdisk.html")
to try to figure out how to get your windows partition loaded so we can edit the registry that way.

---

### Post by jejunum on 2007-05-25
> **BHelts said:**
> did you rename the _registry_machine_***** to *****?
SECURITY.LOG will not work, if there is no SECURITY, rename the SECURITY.old in windows\system32\config back to SECURITY


yes i did, there is a file still called security (renamed the old one, and used _REGISTRY_MACHINE_SECURITY to replace it.)

---

### Post by BHelts on 2007-05-25
ok, so we need to figure out what the bsod is.  check out the link i posted previously and see if you can get the registry loaded so you can change HKLM\.......\CrashControl set back to 0.

---

### Post by jejunum on 2007-05-25
> **BHelts said:**
> ok, so we need to figure out what the bsod is.  check out the link i posted previously and see if you can get the registry loaded so you can change HKLM\.......\CrashControl set back to 0.

I think the problem is some how the drive is not being seen correctly any more.  neither windows (install) or ubcd could see any harddrive.

regedit using wine?  thoughts?

---

### Post by BHelts on 2007-05-25
If you set the windows partition back to read only, does that help?

---

### Post by jejunum on 2007-05-25
> **BHelts said:**
> If you set the windows partition back to read only, does that help?

sorry help regarding what?  
the bsod?  i can load regedit in wine. & i dont see crash control

---

### Post by BHelts on 2007-05-25
when you load regedit in wine, can you double click on HKEY_LOCAL_MACHINE, then double click on System, then double click on CurrentControlSet then double click on Control and then double click on CrashControl?

---

### Post by jejunum on 2007-05-25
> **BHelts said:**
> when you load regedit in wine, can you double click on HKEY_LOCAL_MACHINE, then double click on System, then double click on CurrentControlSet then double click on Control and then double click on CrashControl?

i can, there was no crash control ... i added a new key for it, and reset into windows -still reset! 
im starting to lose it.  Thanks for your patience!

---

### Post by Happy_Man on 2007-05-25
Jeez... I'm learning how to troubleshoot Windows on a Linux forum. This community rules... :D

---

### Post by jejunum on 2007-05-25
> **Happy_Man said:**
> Jeez... I'm learning how to troubleshoot Windows on a Linux forum. This community rules... :D

ugh but some how linux has sorta ruined my ntfs parition.  If i try to run windows install - it can see any thing then BSOD's with a page_fault_in_nonpaged_area   error.

Of course I can read all my data in linux.  bleh bleh bleh

---

### Post by BHelts on 2007-05-25
ok... sorry.  open the registry in wine and do a search for AutoReboot.  if you find it, right click and click on modify, then change the value data to 0.  that will cause the blue screen to freeze so we can get more information. 
i just read you are getting PAGE_FAULT_IN_NON_PAGED_AREA ?  is this true.  if that is the case, it is a memory allocation error and is probably caused by malware or an installation gone bad.  let me know if you find "AutoReboot"
> 
Jeez... I'm learning how to troubleshoot Windows on a Linux forum. This community rules... 

i am a systems administrator and support exclusively windows, and this is the kind of thing i do all day.  but it is also the reason i personally use linux exclusively.  unfortunately for me, people like the kind and gifted people in this forum make it impossible to make a living supporting linux.  but of course, Windows keeps me up to my Registry in clients.

---

### Post by jejunum on 2007-05-25
> **BHelts said:**
> ok... sorry.  open the registry in wine and do a search for AutoReboot.  if you find it, right click and click on modify, then change the value data to 0.  that will cause the blue screen to freeze so we can get more information. 
i just read you are getting PAGE_FAULT_IN_NON_PAGED_AREA ?  is this true.  if that is the case, it is a memory allocation error and is probably caused by malware or an installation gone bad.  let me know if you find "AutoReboot"


i am a systems administrator and support exclusively windows, and this is the kind of thing i do all day.  but it is also the reason i personally use linux exclusively.  unfortunately for me, people like the kind and gifted people in this forum make it impossible to make a living supporting linux.  but of course, Windows keeps me up to my Registry in clients.

I got that read error when trying to reinstall windows -(in the screen when selecting what partion to go on to)   basically windows & other applications (like registry editor on ultimate boot cd) cant see ANY partitions, including NTFS --- which ubuntu can see and edit!


So at this point it feels like some how my windows boot is corrupted...no idea how or why though.

---

### Post by BHelts on 2007-05-25
please post the output of
```
sudo fdisk -l
```
that is a lower case L

---

### Post by jejunum on 2007-05-25
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7          12369    99305797+   7  HPFS/NTFS
/dev/sda3           12370       13585     9767520    c  W95 FAT32 (LBA)
/dev/sda4           13586       14593     8096760    5  Extended
/dev/sda5   *       13586       14544     7703136   83  Linux
/dev/sda6           14545       14593      393561   82  Linux swap / Solaris

---

### Post by BHelts on 2007-05-25
well.... your windows partition is there, as proven by the fact that ubuntu can see it.  i can not explain why ubcd or the repair console do not see a disk.  perhaps there is someone more knowledgeable than I that can help.

---

### Post by jejunum on 2007-05-25
bump: please see first post for conjecture and other people having the same? 
then fix it for me! haha :(

---

### Post by jejunum on 2007-05-26
hopeful bump?

---

### Post by kramer3d on 2007-05-27
I too have the same problem on my Dell Insipron laptop. I will try methods disussed above and get back to this thread... wish me luck ;)

---

### Post by niejan on 2007-05-27
I have the same problem - BSOD saying UNMOUNTABLE_BOOT_VOLUME on ThinkPad T40.

I spent alot of time trying to make it work - but there is no way. I tried to install Debian and I got the same result. I installed Windows and Debian 2 weeks ago on Dell Inspiron and it works perfectly.

So I think its the problem with Windows (XP prof in my case). Windows doesnt read the partition table after modifying it in Linux, maybe some drivers are missing.
I tried to instal Windows after Linux but after modyfing the partition table Windows doesnt see new Linux partitions so it is trying to overwrite them.

---

### Post by jejunum on 2007-05-27
> **niejan said:**
> I have the same problem - BSOD saying UNMOUNTABLE_BOOT_VOLUME on ThinkPad T40.

I spent alot of time trying to make it work - but there is no way. I tried to install Debian and I got the same result. I installed Windows and Debian 2 weeks ago on Dell Inspiron and it works perfectly.

So I think its the problem with Windows (XP prof in my case). Windows doesnt read the partition table after modifying it in Linux, maybe some drivers are missing.
I tried to instal Windows after Linux but after modyfing the partition table Windows doesnt see new Linux partitions so it is trying to overwrite them.

I use xp prof as well :/
take a look at this [https://bugs.launchpad.net/ubuntu/+bug/25451](https://bugs.launchpad.net/ubuntu/+bug/25451)
and see if it might help you

I am going to copy my windows partition on to an external hd (from ubuntu) and see If i can boot up on it.

---

### Post by niejan on 2007-05-27
Thanks for your help. You helped me alot :) and let me save a lot of time. Currently Ubuntu/Winxp works perfectly on my ThinkPad.

---

### Post by jejunum on 2007-05-27
> **niejan said:**
> Thanks for your help. You helped me alot :) and let me save a lot of time. Currently Ubuntu/Winxp works perfectly on my ThinkPad.

yay!  now fix my problem ahahah

---

### Post by TravMan63 on 2007-05-31
jejunum - have you made any progress yet?

Have you tried creating a log file (F8 during 'pre' boot)?

Other info that may help:

[http://support.microsoft.com/kb/307545/en-us](http://support.microsoft.com/kb/307545/en-us)

TM

---

### Post by jejunum on 2007-06-01
> **TravMan63 said:**
> jejunum - have you made any progress yet?

Have you tried creating a log file (F8 during 'pre' boot)?

Other info that may help:

[http://support.microsoft.com/kb/307545/en-us](http://support.microsoft.com/kb/307545/en-us)

TM

no progress.  recovery console is seemingly useless to me because it cant read my c drive.

---

### Post by jejunum on 2007-06-02
i think i figured out the why in my problem, havent tried to fix it yet.

[http://wiki.linux-ntfs.org/doku.php?id=contrib:relocntfs](http://wiki.linux-ntfs.org/doku.php?id=contrib:relocntfs)
[http://www.dominok.net/en/it/en.it.clonexp.html](http://www.dominok.net/en/it/en.it.clonexp.html)

from the second link "Another little nastiness with XP is that it "remembers" its surroundings. It doesn't only keep track of the systems hardware and moans if "too much" of it is altered but also stores data about the partitions it's "surrounded" by in its registry-key"

Since my partition table did change, perhaps this is why.  I hope so atleast.

---

### Post by Lucifiel on 2007-06-02
Wow, this sounds tough. 

It's a pity I don't know enough about Windows to help you, though. 

Best of luck troubleshooting your issue. :) May your Windows get fixed.

---

### Post by kramer3d on 2007-06-04
please please reply if you have solution... am eagerly waiting :P

---

### Post by jejunum on 2007-06-06
> **kramer3d said:**
> please please reply if you have solution... am eagerly waiting :P

havent had a chance to work on it (studying for a board exam) you read/try the above links?

---

### Post by kramer3d on 2007-06-15
yes I have and the closest I got was the thinkpad thingy where you diable something in the bios. But that is of no help to me because I am on a Dell Inspiron 630m and the BIOS doesnt have such a feature. I am also stuck just like you :(

---

