---
title: "removing ubuntu"
date: 2005-07-07
forum: Absolute Beginner Talk
---

### Post by mcflyxc23 on 2005-07-07
I installed ubuntu on an empty hard disk drive.  I keep trying to figure out how to uninstall it completely but am ever so incapable of finding the right way.  How do I unistall ubuntu so the only operating system left on my computer again is Windows XP?  please help! :D

---

### Post by filemanager on 2005-07-07
[QUOTE=mcflyxc23]I installed ubuntu on an empty hard disk drive.  I keep trying to figure out how to uninstall it completely but am ever so incapable of finding the right way.  How do I unistall ubuntu so the only operating system left on my computer again is Windows XP?  please help! :D[/QUOTE]
 If you have a Windows boot disk, put it in and make sure in the BIOS its set to read the disk first before booting off the hard drive, then at the prompt type:

format [driveletter]:

so if Ubuntu is on drive D then format d:

That's how I did it (before I reinstalled).

---

### Post by mcflyxc23 on 2005-07-07
ok, i have the boot disk.  I went and started everything up and it loaded the XP installer but there was no option for me to format the [D] drive.  It wanted to install it on my other drive that al;ready has my working XP.  DO you have any more advice?

---

### Post by filemanager on 2005-07-07
[QUOTE=mcflyxc23]ok, i have the boot disk.  I went and started everything up and it loaded the XP installer but there was no option for me to format the [D] drive.  It wanted to install it on my other drive that al;ready has my working XP.  DO you have any more advice?[/QUOTE]
 Ah, I used the Windows 98 boot disk. If you want I can email you the files and you can just save them onto a floppy disk. (I don't know why, WinXP boot disks just don't work as well)

---

### Post by camp on 2005-07-07
[QUOTE=mcflyxc23]I installed ubuntu on an empty hard disk drive.  I keep trying to figure out how to uninstall it completely but am ever so incapable of finding the right way.  How do I unistall ubuntu so the only operating system left on my computer again is Windows XP?  please help! :D[/QUOTE]


Hi there,

That's a shame!... I probably wouldn't need to help you getting it off!   ;-) 
But the only thing that you have to do... is tog in in to your Microcrap XP, click on start, right click on "your computer" and choose manage.
Then a windows will pop up... with a lot of choices... choose disk management... you will see a schematic of your hard drive and partitions... those partitions that it says "unknown" are your ubuntu partitions. Just right click again, and choose format.

I think this has to work.... Be careful though!!! Even if I prefered it...  :smile:  don't go and wack of your windows partitions!

/JCamp

---

### Post by filemanager on 2005-07-07
[QUOTE=camp]Hi there,

That's a shame!... I probably wouldn't need to help you getting it off!   ;-) 
But the only thing that you have to do... is tog in in to your Microcrap XP, click on start, right click on "your computer" and choose manage.
Then a windows will pop up... with a lot of choices... choose disk management... you will see a schematic of your hard drive and partitions... those partitions that it says "unknown" are your ubuntu partitions. Just right click again, and choose format.

I think this has to work.... Be careful though!!! Even if I prefered it...  :smile:  don't go and wack of your windows partitions!

/JCamp[/QUOTE]
 When I tried that on my computer it said "Cannot format a non-fat32 partition". It was weird :P

But if it works for you go for it!! :)

---

### Post by aysiu on 2005-07-07
There may not be an easy way to go about doing this without potentially damaging your current Windows installation. Are you willing to reinstall Windows?

If so, install Ubuntu again (I know you're trying to uninstall it, but this is a means to an end), but have it wipe out your entire hard drive.

Then, reinstall Windows completely and have it wipe out the entire hard drive. Should get rid of any prior partitioning.

---

### Post by mcflyxc23 on 2005-07-07
how would it damage windows when it is on a completely different hard disk.  Windows is on C and Ubuntu is on D?  I'm getting confused and that's not habitual either....

---

### Post by mcflyxc23 on 2005-07-07
how do i delete that grub sys dual boot program so that I don't get like an "error 17" code while my computer loads after formatting my ubuntu drive.  Thankfully I reinstalled ubuntu and it all worked again so I didn't have to format my windows drive.  Does anyone have any thorough explanation on this matter of removing ubuntu (on a seperate disk drive) without disrupting my current windows xp configuration

---

### Post by skirkpatrick on 2005-07-08
What about just using fdisk (from booting a DOS floppy) and deleting the partition Ubuntu is on?

---

### Post by camp on 2005-07-08
[QUOTE=skirkpatrick]What about just using fdisk (from booting a DOS floppy) and deleting the partition Ubuntu is on?[/QUOTE]

Yes, I think this should do the trick!
I'm not to sure about it.... but running FDISK /MBR should wipe out the firsts disk MasterBootRecord... If I recall right, Windows doesn't need it. It even erase it if present during an installation. That's the reason why you always should instal MicrocrapOS first, and then Linux on a DualBoot machine.

Any of you guys agree!?

/JC

---

### Post by skirkpatrick on 2005-07-08
Agree on both resetting the MBR and that Windows should be installed first.

---

### Post by mcflyxc23 on 2005-07-09
does anyone have the win98 startup disk files they could send to me by e-mail?  If so please send them to [email]rjmacneely@gmail.com[/email].  I would really appreciate it.

---

