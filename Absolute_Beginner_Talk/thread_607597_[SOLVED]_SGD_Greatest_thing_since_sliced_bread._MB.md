---
title: "[SOLVED] SGD Greatest thing since sliced bread. MBR problems"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by spideygal on 2007-11-09
I hardly ever use Windows anymore but decided to clean up my Windows as it is on a separate partition. Anyways, I edited the boot.ini file and then tried to use easyBCD as well. I completely screwed up booting into windows so I decided to add a second windows directory and that re-wrote 
my MBR and then I was kept out of Ubuntu, and that was really frightening.

My new Windows XP could not even connect out of the box to the Internet. I did not spend any time there as I have a router and modem to configure so I booted into the Feisty live CD but I was not able to edit my menu.lst file despite using sudo commands from terminal or gksu nautilus. But I could surf and first place I went to was these forums and did a search on Grub and the was a link to a site all about Grub and I read it and tried a few things but nothing really worked but at the end I read about Super Grub Disk, what a life saver.


Super Grub disk made it so simple to boot my Ubuntu install, I then went to my menu.lst and deleted this at the end as this was causing my troubles.

```
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

As you can see, I had the Vista/Longhorn loader and the Vista is non existant because it was the beta and I removed that and have my fresh install of Feisty in it's place.

So I had a dilemna all the way around, EasyBCD is just for Vista and that screwed up since I can not use it with XP, but I did get a net framework that allowed me to use it and I messed up and now this is getting really long winded so let me wrap it up.

I did all this because I thought the grub only pointed to the Windows OS and I thought if I screwed it up, I could just default to Ubuntu. 

The boot error I got was to replace the System32 hal.dll but that dll is there. From what I have read is that that error only means you have screwed up the MBR. So what to do now? Can I edit the boot.ini to reflect what was in my original or do I need to replace the hal.dll. 

Replacing the dll is not going to edit the MBR.

Need some help but am happy as can be to be in Ubuntu and real big KUDOS to Super Grub Disk.  That was a piece of cake!

---

### Post by spideygal on 2007-11-09
I guess my spidey senses are not prevailing as well as they use to. I thought I would have an answer by the time I awoke from my beauty sleep.

Bumping to get some help on how to edit my MBR from Linux if at all possible, see above post.

Thank you, 

SG

---

### Post by kellemes on 2007-11-09
The hall.dll-issue *may* be fixed by issuing "fixboot" from recovery-console as far as I know. (type "help" for all the commands.)
It has something to do with boot.ini and not specifically the MBR.
You can also use fixmbr but I think this won't fix the hall.dll-problem and after this you need to restore Grub with SuperGrubDisk.

---

### Post by natehatewindows on 2007-11-09
sliced bread is way over-rated :)

---

### Post by spideygal on 2007-11-09
> **kellemes said:**
> The hall.dll-issue *may* be fixed by issuing "fixboot" from recovery-console as far as I know. (type "help" for all the commands.)
It has something to do with boot.ini and not specifically the MBR.
You can also use fixmbr but I think this won't fix the hall.dll-problem and after this you need to restore Grub with SuperGrubDisk.


Last night after I was in horror shock and could not find things. I installed a second Windows directory named Windows2. It is stripped down to the bone Windows XP and can not get Internet (Yet)

I read this below so I assume this is what you are talking about.

1.	Insert the Windows XP CD into the CD-ROM drive.
2.	Click Start, and then click Run.
3.	In the Open box, type d:\i386\winnt32.exe /cmdcons where d is the drive letter for the CD-ROM drive.
4.	A Windows Setup Dialog Box appears. The Windows Setup Dialog Box describes the Recovery Console option. To confirm the installation, click Yes.
5.	Restart the computer. The next time that you start your computer, "Microsoft Windows Recovery Console" appears on the startup menu.

If so this should work ok as my XP that I can boot into is a fresh install without service pack 2

However, I am not sure how to get the boot.ini to be correct for my main install of Windows as it previously had a beta Vista so the Vista bootloader was installed that Grub was using and now that is borked. What do I do to get it back? Try to add what Grub originally had?


Thanks

Sorry for being confused but that is my state of mind right now, if I use the fixboot, I am guessing it will not do the trick for me, because it will try to restore it to original and not the one the Vista beta put in.   ????

---

### Post by spideygal on 2007-11-09
I wanted to add that I did try the recovery method last night from my XP cd but was unable to use it as it wanted me to provide an administrators password.

Not once in all my Windows years did I ever use or sign up for an administrators password, so I was clueless as to what to provide since I never had one!

What to do in this case?

---

### Post by spideygal on 2007-11-09
Well I have been playing around with SGD and it does a lot of things without my knowledge but I was able to boot my previous Windows install. Here is what I have for boot.ini

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS2
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home
Edition" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="OS for testing new boot
screen" /FASTDETECT /NOEXECUTE=OPTIN /KERNEL=NewBoot.exe

Of course I want to remove the default and make partition(2) the default, that part seems simple.

What should I add to menu.lst to boot Windows correctly?


TIA

---

### Post by spideygal on 2007-11-09
Bumping,

What should I enter in to menu.lst if I want it to boot this partition in Windows?

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Micro soft Windows XP Home

Also why is that **rdisk** and the default is just plain **disk**? 

See previous post for above question.

Pretty please, sixty views and no answer and I am getting blonder by the moment.

---

### Post by Duck2006 on 2007-11-09
> it wanted me to provide an administrators password.

If you never provided one just hit enter and it will continue.
What this the output from the ubuntu install in the terminal of

sudo fdisk -l

post the output.

---

### Post by spideygal on 2007-11-09
Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        3628    29109780    7  HPFS/NTFS
/dev/sda3            3629        4937    10514542+   7  HPFS/NTFS
/dev/sda4            4938        4998      489982+   5  Extended
/dev/sda5            4938        4998      489951   82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3493    28057491   83  Linux
/dev/sdb2            3494        3649     1253070    5  Extended
/dev/sdb5            3494        3649     1253038+  82  Linux swap / Solaris

Disk /dev/sdf: 1005 MB, 1005060096 bytes
48 heads, 48 sectors/track, 852 cylinders
Units = cylinders of 2304 * 512 = 1179648 bytes
[U]
   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         851      979912+   6  FAT16[/U]


I just ran this command before you posted, thanks for any help as this has my head in Knots.  PS forget about the last boot entry underlined as I was just trying to make a SGD on a USB but have it on CD now.

---

### Post by Duck2006 on 2007-11-09
In your menu.lst make this entry

title Microsoft Windows
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

---

### Post by spideygal on 2007-11-09
Thanks much, keeping my fingers crossed as I reboot.:)


Worked perfect. Thanks again.

---

### Post by adrian15 on 2007-11-15
> **spideygal said:**
> Well I have been playing around with SGD and it does a lot of things without my knowledge.

Which options did you use to say that? What are the things that SGD does without your knowledge and that you should be aware of?

Thank you.

adrian15

P.S.: I prefer non-sliced bread, it tastes better. ;)

---

