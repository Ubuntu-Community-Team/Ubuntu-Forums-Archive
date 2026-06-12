---
title: "To Stay with Ubuntu or not."
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by taipan899 on 2006-11-10
Hi all,

I know this is a bit of a winge but what the hell.

I was a very happy V5 user of ubuntu until the up grade(s) came out. Waiting about 2 months I decided to upgrade to V6 and that to me has been the cause of my problems.

During the first upgrade it froze and came up with a message that the upgrade had failed and please forward a copy of the ??? file to  whoever. This would have been wonderful but my hard drive was now corrupted and would not boot, in fact it would not even reformat so I was unable to send the report.:( 

I then decided to grab one of my old hard drives. Tested it, reformatted it in NTSF, it seemed OK so I tried again to install V6 and got the same result.]:roll eyes: 

Ok, down to the shop and purchase a new hard drive. Installed windows 2000, tried to recover hard drives no luck:mad: 

Oh, well I thought it must have been the drives as everything else tested OK under windows. No apparent overheating showing.

Guess what? Same result:confused: 

Rang a techi friend his only suggestion was that the processor may be over heating/faulty or a mother board fault.:confused: 

Now no computer:( 

So out with the old and in with the new.

Ordered a copy of the offical "Ubuntu" book with Ubuntu 6.06 LTS disk.

Having two hard drives I formatted C: and installed 2000 on drive C:. I now have a computer again:D 

I then decided to install V6 again. This time the system would not boot started to load kernal then hung. After some fiddling I decided that V6 was not going to load onto my new machine.:eek: 

Ok, the next best thing would be to reinstall V5. and you guessed it the bloody thing would not install. Ran the kernal and after waiting a while, I pushed Ctrl-Del-Shift the board gave three beeps and closed down the machine.

While I love Ubuntu I have only limited resources both time and financial, so the question is? Should I persever with Ubuntu (My preferred choice) or simply ditch it for Windows which would make me.:( .

My new system basically consists of:

2X Western Digital 80/7200 SATA drives,
1X Intel Core Duo 2.13 GHz 2Mb Cache,
1X Intel D9426DZIssl Core 2 Motherboard,
2X 512 DDRM Ram2 533 Dual Chanel 533MHz memory. 


Any and all help greatly appreciated.

Sid Prendergast
Taipan899

---

### Post by angryfirelord on 2006-11-10
Sounds like to me that you're trying to install Ubuntu on a NTFS partition (though I may be wrong because I read things the wrong way). Use ext3 or equivalent instead.

---

### Post by Jakk on 2006-11-10
Here are some ideas that might be helpful. The Ubuntu install CD could be corrupted. Did you burn it yourself? If so, you could try to burn it at a slower speed. You can format your hard drive without installing Windows. You can tell Windows to reformat your hard drive during the install process and once that is done you can shut down your computer and you have a refortatted hard drive. You can also try Partition Magic to create, delete, and format partitions. And you can also use it to create Linux Swap and EXt3 partitions. You can also try fdisk for windows, it's free. Windows has a tool called Disk Management located in Windows/Sytem32, I believe, that can also reformat, delete and create partitions.

---

### Post by Sef on 2006-11-10
> You can also try Partition Magic to create, delete, and format partitions.

Don't use Partition Magic. It and GNU/Linux do not get along well. Instead use [GParted]("http://GParted.sourceforge.net").  It is a graphical installer and no cost.

---

### Post by Drakkor on 2006-11-10
Easiest way is to do it with the GParted live disk and just allocate free space and clean install dapper or edgy on it. I've seen alot of problems with people trying to upgrade from version to version, a clean install seems to me
a better option.

---

### Post by Jakk on 2006-11-10
> **Sef said:**
> Don't use Partition Magic. It and GNU/Linux do not get along well. Instead use [GParted]("http://GParted.sourceforge.net").  It is a graphical installer and no cost.

He mentioned that he couldn't install Ubuntu at all, only Windows 2000. That is why I told him about Partition Magic, a Windows app. I don't know if GParted is only a Linux app or can be used in Windows too.

---

### Post by scrooge_74 on 2006-11-10
I had some trouble with an NTFS partioned disk.  I got myself a second hand Toshiba laptop that had XP on it.  First I was thinking on dual boot.  But when I try to repartion the harddrive using the Ubuntu CD it would hang half way throught.  

In the end since i did not had much use for XP, i just made the Live CD erase the entire disk and make a clean install.  So I only have 6.06 installed and have been very happy with the results of the last month.

I was previously using Debian 3.1, but I wanted to try Ubuntu.

---

### Post by kinematic on 2006-11-10
> **taipan899 said:**
> I then decided to grab one of my old hard drives. Tested it, reformatted it in NTSF, it seemed OK so I tried again to install V6 and got the same result

](*,)  :-k  [-(  :confused:

---

### Post by Drakkor on 2006-11-10
You boot to the GParted live disk and you can repartition and format any drive you want...including Winbloze :mrgreen:
I would just leave unallocated space,then tell Ubuntu to install to the biggest continuous free space ! Good Luck !

---

### Post by kinematic on 2006-11-10
and don't use ntfs

---

### Post by rbprogrammer on 2006-11-10
> **Sef said:**
> Don't use Partition Magic. It and GNU/Linux do not get along well. Instead use [GParted]("http://GParted.sourceforge.net").  It is a graphical installer and no cost.
why do you say they dont get along? i dont use partition magic often, but when i do there are never any problems because of it.  at least for me, and then again i dont use it often....

---

### Post by Drakkor on 2006-11-11
It really pains me to see that you just have negatives to say, why don't you try to help the guy,like we all have,instead of flinging accuusations ??

---

### Post by igknighted on 2006-11-11
Ahh, one of the many beauties of linux... If you are having issues with Ubuntu, there are hundreds more distro's to choose from.  I probably install 2 new distro's per week on my testing HD's, just to try them out.  The hardware detection varies from distro to distro, so the best advice I can give is keep trying distro's until you find one that works and fits your needs well.  Ubuntu is very good, but Linux is never one size fits all.  It isn't right for everyone.  Explore around.

---

### Post by tstrowd on 2006-11-11
I know his pain. I tried the new version of Xubuntu because of the older machine i have and the install locked up. Strange it never locked in the same place though. I tried installing it multiple times. So i went back to Ubuntu 5.04 and not a problem.

---

### Post by taipan899 on 2006-11-11
First of all, A BIG THANK YOU  to all have tried to help me. :D

Sorry I have caused some is some confusion re the hard drives.

On the old machine I reformatted in NTFS to help check that the old drive was still working and not corrupted. When installing Ubuntu V6 I used auto and or ext3 to try to get the drive to install Ubuntu but once I had tried once the installer refused to see the hard drive.

On the new machine I do not ever get that far as the computer freezes before I even get to a start menu in both V5 and V6. All I get is the copmuter starting to load the kernal. the it hangs.

Sorry if I confused you.

Many thanks for your replies.

Sid Prendergast
Taipan899

---

### Post by IanGB on 2006-11-11
I disagrree with you here Sef. Partition Magic 8 will happily format Ext2 & Ext3 ready for a linux install.



It will also sort out the two partitions for Win and Linux with ease.

---

### Post by Sef on 2006-11-11
> I disagrree with you here Sef. Partition Magic 8 will happily format Ext2 & Ext3 ready for a linux install.

Maybe they have got it working well with Linux, but until I hear more about that, I won't recommend it.  There have been too many threads on too many forums for me to recommend it.

Also it costs at around $70.00.  GParted is no cost. For someone with a tight budget, the choice is easy.  If you have the money and like it, get it.  The choice is yours.  Neither choice is wrong.

---

### Post by Steve Baker on 2006-11-11
This may be a silly question (and I am an Ubuntu newbie) but...  Should he be installing the 1386 or the AMD64 version?  Perhaps this is the source of his problem.  I mean, it seems to me that a problem has popped up on several hard drives, two computers and, if I'm reading correctly, two different Ubuntu source disks - the burned CD and the DVD from the book.  There has to be something in common across the board. Hmmm.  It would be the i386 version, wouldn't it?

---

### Post by Cynical on 2006-11-11
I disagree about partition magic. I ran the program once to see what it was like and it said that there were several parameters for my hard drive that werent correct and offered to fix them for me. I agreed and it decided to corrupt my partition table. And gparted is perfectly fine for his situation anyway.


Try to boot your computer again and when you see the grub list press E, and then press E again to edit the line with your kernel on it. At the very end of the line, add

```

apci=off nolapic

```

---

