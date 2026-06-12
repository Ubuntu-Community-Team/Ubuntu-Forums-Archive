---
title: "setting up a dual boot system"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by RAV TUX on 2006-04-13
I am setting up a dual boot system on a computer using Windows XP Sp2.

I was just reviewing my Windows XP's Disk Management tool...

[http://img142.imageshack.us/img142/546/041320062139052ka.jpg](http://img142.imageshack.us/img142/546/041320062139052ka.jpg)

I want to set it up so that Ubuntu can both read and write files to partition. So I need to convert NTFS Windows partition to FAT32. 

I was wondering which is the best third party disk partitioning program? Are there better options beyond Symantec's Partition Magic to convert your file system?

What have other people used here or is there a better way to convert to FAT32?

...and can somebady please explain the difference in basic terminology for me?

---

### Post by ajmoncrief on 2006-04-13
Good luck converting from NTFS to FAT32.  When I researched the material, I dont think that it was possible (may be different now).  Seems like I remember being cautioned against even trying because it was a risky procedure.

[http://faq.arstechnica.com/link.php?i=1820](http://faq.arstechnica.com/link.php?i=1820)

You may want to partition some free space into fat32, copy everything from the ntfs to fat32, then wipe out the ntfs.  Worked for me.





[QUOTE=yozef]I am setting up a dual boot system on a computer using Windows XP Sp2.

I was just reviewing my Windows XP's Disk Management tool...

[http://img142.imageshack.us/img142/546/041320062139052ka.jpg](http://img142.imageshack.us/img142/546/041320062139052ka.jpg)

I want to set it up so that Ubuntu can both read and write files to partition. So I need to convert NTFS Windows partition to FAT32. 

I was wondering which is the best third party disk partitioning program? Are there better options beyond Symantec's Partition Magic to convert your file system?

What have other people used here or is there a better way to convert to FAT32?

...and can somebady please explain the difference in basic terminology for me?[/QUOTE]

---

### Post by jimrz on 2006-04-13
Not familiar with any of the others, but Partition Magic worked great for me.
Looking at your screen shot it appears that:

1- PM should have no prob converting your ntfs, since you have plenty of unused space for it to use should you go ahead with that option.

2- You have lots of drive space so you could alternatively shrink your ntfs "basic windows partition and then use the newly created "unallocted space" to create your "/" partition for ubuntu and an extended partition in which you could create your "/home" partition for ububtu + your linux swap partion and a large FAT32 partition, in which you could keep all of your files (music/video/office stuff/ pics or whatever) that you would want to be able to access from either OS. 

   Should you go with #2 as I did (and it has worked out quite well), you would want to:

1-  create partitions for "/" and "/home" with PM but not format them. Allow the ubuntu install to do that. "ext3" is the default file system and it is doing fine for me.

2- leave some "unallocated space" ( roughly 1.5-2x the amount of RAM that your machine has installed) and allow the installer to build your "swap" here.

3- create AND format your FAT32 partition

4- check out [[COLOR="Sienna"]**_this_**[/COLOR]]("http://users.bigpond.net.au/hermanzone/") excellent guide to dual boot installation. It gives quite explicit instructions including how to correctly handle the partitioning portion of the install.

Welcome to ubuntu.

EDIT: looking at your screenshot again, you probably need to know what the other 2 basic partions on your drive are (probs some sort of recovery utility on the larger one and ??? for the smaller) and whether or not they are really needed. If they are, you may need to, since I beleive you can only have 4 ( 3 primary + 1 extended, which can contain many partitions) partions on a single drive, have to put "/" ( I beleive that this can work, but check further sources to be sure) in the extended partition, as well.

---

### Post by RAV TUX on 2006-04-13
[QUOTE=ajmoncrief]Good luck converting from NTFS to FAT32.  When I researched the material, I dont think that it was possible (may be different now).  Seems like I remember being cautioned against even trying because it was a risky procedure.

[http://faq.arstechnica.com/link.php?i=1820](http://faq.arstechnica.com/link.php?i=1820)

You may want to partition some free space into fat32, copy everything from the ntfs to fat32, then wipe out the ntfs.  Worked for me.[/QUOTE]


:confused: When did you attempt to do this? and did you use Partition Magic? if so what version? 

I was just reviewing the Key features of Partition Magic:

Key Features

    * Divides a single hard drive into two or more partitions
    * Lets you safely run multiple operating systems on the same PC
    * BootMagic™ makes it easy to switch between different operating systems
    * Allows you to copy, move, resize, split, or merge partitions as neededwithout losing data
    * How-to wizards guide you step by step through the partitioning process
    * Intuitive Windows®-based browser lets you find, copy and paste files in both Windows and Linux® partitions
    * Allows you to create and modify partitions up to 300 GB*
    * Supports USB 2.0, USB 1.1, and FireWire® external drives**
    * Supports FAT, FAT32, NTFS, Ext2, and Ext3 file systems
    * Converts partitions among FAT, FAT32, and NTFS without losing data
    * Allows you to enlarge an NTFS partition without restarting your computer
    * Resizes NTFS system clusters to the most effective size


* Supports operations on partition sizes as large as 300 GB when partition is less than 90% full. Larger hard drives may require additional memory.


:???:  I realize the drawbacks on the above program. Qoute from you link
"...shelling out for a third-party program. Unfortunately, Windows does not have a built-in tool to convert backwards, like one can to convert from FAT/FAT32 to NTFS. Enter Partition Magic. Partition Magic allows you to convert an NTFS partition back to FAT32, but there is a reason that Partition Magic is not so lovingly referred to as "Partition Tragic"."

...but they forgot to reference which version was used?

has anybody have any experience with this program? I would hate to shell out money for it if it doesn't work, if it works I don't mind paying, but has anybody developed an open source alternative to this that simply works without having to pay the piper again?

:confused: Also, ajmoncrief I am a beginner  how did you implement your solution?


:confused: A bigger question is it really necessary to be able to do this? Should I just leave everything in NTFS or does Ubuntu need FAT or FAT32...it appears that 87% of my system is in NTFS.

---

### Post by RAV TUX on 2006-04-13
[QUOTE=jimrz]Not familiar with any of the others, but Partition Magic worked great for me.
Looking at your screen shot it appears that:

1- PM should have no prob converting your ntfs, since you have plenty of unused space for it to use should you go ahead with that option.

2- You have lots of drive space so you could alternatively shrink your ntfs "basic windows partition and then use the newly created "unallocted space" to create your "/" partition for ubuntu and an extended partition in which you could create your "/home" partition for ububtu + your linux swap partion and a large FAT32 partition, in which you could keep all of your files (music/video/office stukk/ pics or whatever) that you would want to be able to access from either OS. 

   Should you go with #2 as I did (and it has worked out quite well), you would want to:

1-  create partitions for "/" and "/home" with PM but not format them. Allow the ubuntu install to do that. "ext3" is the default file system and it is doing fine for me.

2- leave some "unallocated space" ( roughly 1.5-2x the amount of RAM that your machine has installed) and allow the installer to build your "swap" here.

3- create AND format your FAT32 partition

4- check out [[COLOR="Sienna"]**_this_**[/COLOR]]("http://users.bigpond.net.au/hermanzone/") excellent guide to dual boot installation. It gives quite explicit instructions including how to correctly handle the partitioning portion of the install.

Welcome to ubuntu.[/QUOTE]

:) jimrz Thanks for the excellent response(I posted the other response before seeing your post)....So I will follow your advice and utilize Partition Magic...and follow your other advice for what has worked for you...

again Thank You and I hope I can contact you if I have further questions....

---

### Post by RRS on 2006-04-13
[QUOTE=yozef]I was wondering which is the best third party disk partitioning program? Are there better options beyond Symantec's Partition Magic to convert your file system?[/QUOTE]

The partitioning tool on the Ubuntu install disc works quite well. Select "manual" when the installation gets to that stage.

I've also heard of some problems with Partition Magic though I've never used it myself and couldn't say.

> Good luck converting from NTFS to FAT32. When I researched the material, I dont think that it was possible (may be different now). Seems like I remember being cautioned against even trying because it was a risky procedure.

[http://faq.arstechnica.com/link.php?i=1820](http://faq.arstechnica.com/link.php?i=1820)

You may want to partition some free space into fat32, copy everything from the ntfs to fat32, then wipe out the ntfs. Worked for me.

Will XP still boot after being copied into fat32?

> 4- check out this excellent guide to dual boot installation. It gives quite explicit instructions including how to correctly handle the partitioning portion of the install.

Second that, excellent guide!

Also, Defrag XP to save some space and back-up(just in case) before installing Ubuntu.

Welcome Aboard :)

---

### Post by jimrz on 2006-04-13
Yozef - you are more than welcome. This is what these forums and ubuntu , in general, are all about. I certainly have received more assistance and learned more here than I could ever give back. You are certainly welcome to contact me via this thread / instant msgs/ or pm through the forum, if needed.

  I have in the past (last year, I beleive) used PM to convert ntfs to FAT32 on another system using PM and it worked out well. However, I strongly recommend #2 since it acheives what you are wanting and allows your basic win partiton to remain ntfs, which I am told is better for xp (or 2k) for whatever reasons.

---

### Post by jimrz on 2006-04-13
[QUOTE=RRS]The partitioning tool on the Ubuntu install disc works quite well. Select "manual" when the installation gets to that stage.

I've also heard of some problems with Partition Magic though I've never used it myself and couldn't say.



Will XP still boot after being copied into fat32?



Second that, excellent guide!

Also, Defrag XP to save some space and back-up(just in case) before installing Ubuntu.

Welcome Aboard :)[/QUOTE]

OOPS- Thanks RSS...I failed to point out the need to defrag (maybe a couple of times) and that is essential. Also, yes xp will run on FAT32, although you lose the indexing capabilties of ntfs. I have one that does so without problems, but am not sure that would be true after converting from ntfs. xp was installed to FAT32 on an older laptop in order to maximize use of a smallish drive running a dual boot.

---

### Post by RAV TUX on 2006-04-14
[QUOTE=jimrz]Yozef - you are more than welcome. This is what these forums and ubuntu , in general, are all about. I certainly have received more assistance and learned more here than I could ever give back. You are certainly welcome to contact me via this thread / instant msgs/ or pm through the forum, if needed.

  I have in the past (last year, I beleive) used PM to convert ntfs to FAT32 on another system using PM and it worked out well. However, I strongly recommend #2 since it acheives what you are wanting and allows your basic win partiton to remain ntfs, which I am told is better for xp (or 2k) for whatever reasons.[/QUOTE]

:) Thanks jimrz I am also glad to come back to the Ubuntu Community and the forums here are the best I have found. 

Ok so in review of your advice I should opt for #2 

"2- You have lots of drive space so you could alternatively shrink your ntfs "basic windows partition and then use the newly created "unallocted space" to create your "/" partition for ubuntu and an extended partition in which you could create your "/home" partition for ububtu + your linux swap partion and a large FAT32 partition, in which you could keep all of your files (music/video/office stukk/ pics or whatever) that you would want to be able to access from either OS.

Should you go with #2 as I did (and it has worked out quite well), you would want to:

1- create partitions for "/" and "/home" with PM but not format them. Allow the ubuntu install to do that. "ext3" is the default file system and it is doing fine for me.

2- leave some "unallocated space" ( roughly 1.5-2x the amount of RAM that your machine has installed) and allow the installer to build your "swap" here.

3- create AND format your FAT32 partition

4- check out this excellent guide to dual boot installation. It gives quite explicit instructions including how to correctly handle the partitioning portion of the install."

So I should leave my current windows space as is...in doing so I should convert the rest of my unallocated space? I have to admit I am a bit confused.:confused:

---

### Post by swawryk on 2006-04-15
Just to add my 2c.  I've used Partition Magic (can't remember the the version for sure but I think it was 2003 or something like it) at work and a very similar tool, Disk Director 10.0 from Acronis at home.

They have very similar capabilities and both worked without any problems for me.  The only reason I got Disk Director for home was that Symeantec didn't bother to answer any of my questions but Acronis were very responsive.:)

---

### Post by RAV TUX on 2006-04-16
ok these are the options I got:

[http://img119.imageshack.us/img119/1920/129206318287955f201b2ac.jpg](http://img119.imageshack.us/img119/1920/129206318287955f201b2ac.jpg)

what do I do?:confused: :confused: :confused:

and when I choose Manually edit, I get this:
[http://img119.imageshack.us/img119/4210/1292063217360210877b4xz.jpg](http://img119.imageshack.us/img119/4210/1292063217360210877b4xz.jpg)


Update: Thanks to my new friend Tom I have found a Linux based Partioning Magic Clone
QT Parted
[http://qtparted.sourceforge.net/faq.en.html](http://qtparted.sourceforge.net/faq.en.html)
also G parted looks good too:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by bodhi.zazen on 2006-04-17
Yozef:

It is confusing to partition and install. You are half way home.

Options:
  1. Resize your Windows (NTFS) partition. This is risky and may fail. Back up your critical data first.
  2. Make a GRUB floppy (in case you can not boot after the install).

[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

At this point you should have 2 spaces on your hard drive:
   1- Windows (NTFS).
   2- Free, unformattted space.


Side track
You can choose to make additional partitions (in the Free space). This can be done with Ubuntu.
  1. Keep Windows in the first partition.
  2. Make the second partion an Extended/Logical partition which will contain at least 2 spaces:
             1. SWAP
             2. "root" or / for Ubuntu

  3. Make a 3rd partionion, primary or Logical does not matter. Format it in FAT (FAT32). This partion will serve as a Data partition and can be accessed from Windows or Ubuntu.

_Optional:_ If you want you can make (in the extended partition):
             1. Additional space for other versions of Linux.
             2. A "home" or /home partition. The above FAT partionion will serve simmilar functions to a /home partition (data storage separate form the root file system).


Back to installing Ubuntu

  2. You will install Ubuntu into the Free space you have created.
  3. On the first screen shot -> chose manually edit partition table.
  4. Ubuntu (Linux) needs a swap space. This shouuld be the size of you RAM X2 (twice the size of your total RAM).
  5. Ubuntu  then needs a "root" partition called /. This will take the rest of your space (after the swap)..
  6. Accept the partition scheme.
  7. Ubuntu will then install.
  8. It is OK to install GRUB to the MBR at this point.
  9. Re-boot.

The problem is Ubuntu will not resize your Windows partition.

You run a (small) risk of losing Data or all of windows when you re-size the partition. Try gparted.

[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/install-guide/s1-x86-dualboot-parted.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/install-guide/s1-x86-dualboot-parted.html)

Good luck, hope this helps.

---

### Post by RAV TUX on 2006-04-19
Thanks bodhi.zazen for the help...unfortunately my job has kept me too busy to proceed I hope to work on it this weekend perhaps...

Thanks for this awesome link:

[http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted](http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted)

:p

---

### Post by RAV TUX on 2006-04-28
[QUOTE=bodhi.zazen]
  2. Make a GRUB floppy (in case you can not boot after the install).

[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

[/QUOTE]

I am downloading an ISO image of "Super Grub Disk"

[http://adrian15.raulete.net/grub/tiki-list_file_gallery.php?galleryId=1](http://adrian15.raulete.net/grub/tiki-list_file_gallery.php?galleryId=1)

I have also figured out how to burn to disk using ISORecorder and have burned a live disk of gparted. 

I am also downloading an ISO.torrent of Ubuntu 6.06 LTS (Dapper Drake) Beta 2

[http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/)

also I have burned 5 disk install of SUSE(just to experiment with)

a great guide on disk partitioning is here:
[http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_Partition_a_Hard_Drive_for_Linux](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_Partition_a_Hard_Drive_for_Linux)

and covers a lot of what you told me....ok...wish me luck...I'll continue to let you know how things progress
:mrgreen:

---

### Post by catlett on 2006-04-28
This doesn't have to be this complicated. Just so you know I have converted my partitions about three times with PM and never had a problem and have shrunk my partiton many times without a problem
I used Partition Magic 8. When you open PM you will see your partiton. Highlight your partition. On the left hand side there are options. Choose "convert". This will convert your partition type. The only issue is the one already mentioned. You have to have as much free space as used space so the data can be moved while one side is converted and then moved back while the other side is converted.
Then put in the install cd. And get to partitioning. (can I make a comment? Why don't you give the second drive to Ubuntu? I see from your images you posted you have 2 hard drives. The easiest install is "erase entire disk, scsi3" choosing that option will set off an automatic formatting and partitioning of the 2nd drive for Ubuntu)
If you need that space for windows and you only want to split some off the other easy way is to "resize your existing partition".

All the advice given earlier is correct and accurate but can be difficult to put into action. The install is not good at clarifying. It can be confusing setting up mount points. So my advice (which is the advice of a Ubuntu beginner) is to make sure you have a current backup of your windows install and then use PM to convert and let Ubuntu do the partitioning. Either give it the entire 2nd drive (scsi3) or resize your windows partition. It is the easier way, albeit a riskier way. I never had data loss but when you move data arouind and format, there is the potential for data loss. Either way good luck.

---

### Post by RAV TUX on 2006-04-28
[QUOTE=catlett]This doesn't have to be this complicated. Just so you know I have converted my partitions about three times with PM and never had a problem and have shrunk my partiton many times without a problem
I used Partition Magic 8. When you open PM you will see your partiton. Highlight your partition. On the left hand side there are options. Choose "convert". This will convert your partition type. The only issue is the one already mentioned. You have to have as much free space as used space so the data can be moved while one side is converted and then moved back while the other side is converted.
Then put in the install cd. And get to partitioning. (can I make a comment? Why don't you give the second drive to Ubuntu? I see from your images you posted you have 2 hard drives. The easiest install is "erase entire disk, scsi3" choosing that option will set off an automatic formatting and partitioning of the 2nd drive for Ubuntu)
If you need that space for windows and you only want to split some off the other easy way is to "resize your existing partition".

All the advice given earlier is correct and accurate but can be difficult to put into action. The install is not good at clarifying. It can be confusing setting up mount points. So my advice (which is the advice of a Ubuntu beginner) is to make sure you have a current backup of your windows install and then use PM to convert and let Ubuntu do the partitioning. Either give it the entire 2nd drive (scsi3) or resize your windows partition. It is the easier way, albeit a riskier way. I never had data loss but when you move data arouind and format, there is the potential for data loss. Either way good luck.[/QUOTE]


Thanks for the help, it is greatly appreciated.

I don't think I have two hard drives?

unless I missed something, which could totally be possible I just recently found out I have a 64bit computer Intel EM64T, I have always wanted a dualcore 64bit computer, and what do you know I already have one.

Now two hard drive would be nice, but not sure how to check?

perhaps through the BIOS, system menu?

I do have two computers. I don't know much about the old one but that it had 98se on it, old Compaq. Ubuntu runs great on it.

Question about partition magic, is that open source? 

:mrgreen:

EDIT: on my new computer I would like to install Ubuntu/Scientific Linux or SUSE/XP(keep for now and eventually free myself from it all together, then load another distro)

---

### Post by bodhi.zazen on 2006-04-29
Hi Yozef, this is a reply to several of your questions.

First, congratulations. It looks as if you are now off and running.

Could you re-phrase any questions you now have??

Looking at your post regarding booting to windows and your grub file:

First of all Windows wants to be in a primary partition (not logical or extended).

Second Windows will over write GRUB in your MBR (Master Boot Record).

So to fix your problem (I am guessing):

1. Boot into Ubuntu.
2. Edit/fix your menu.1st file
     sudo nano /boot/grub/menu.1st 

In your windows entries:

“
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title		Windows NT/2000/XP (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

“
change it to:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title		Windows 2000
root		(hd0,2)
# savedefault
makeactive
chainloader	+1
boot


And

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda4
title		Windows XP
root		(hd0,3)
# savedefault
makeactive
chainloader	+1
boot

3. Save menu.1st
     If using nano ctrl-X, answer yes to ?save

4. Re-install GRUB to the MBR
     sudo grub
     > setup (hd0,0)

I may have the grub commands wrong, check my first post for web site.

Hope this helps.

---

### Post by zeca_pedra on 2006-09-15
> **yozef said:**
> I am setting up a dual boot system on a computer using Windows XP Sp2.

I was just reviewing my Windows XP's Disk Management tool...

[http://img142.imageshack.us/img142/546/041320062139052ka.jpg](http://img142.imageshack.us/img142/546/041320062139052ka.jpg)

I want to set it up so that Ubuntu can both read and write files to partition. So I need to convert NTFS Windows partition to FAT32. 

I was wondering which is the best third party disk partitioning program? Are there better options beyond Symantec's Partition Magic to convert your file system?

What have other people used here or is there a better way to convert to FAT32?

...and can somebady please explain the difference in basic terminology for me?


Converting NTFS to FAT32 it's not possible.
You'll have to backup your files and folders, delete the NTFS partition, create a FAT32 one and format it!
I know because I had to go through that experience after googling a lot for a solution! But formating the partition it's necessary so BACKUP your data first, please!

I also take this opportunity to ask a question. I wanted to have this partition scheme on my laptop:
[LIST]
[*]sda1 - swap - 1.1 GB
[*]sda2 - ext3 (/) - 9.9 GB (with Ubuntu 6.06)
[*]sda3 - NTFS - 24 GB (with Windows XP)
[*]sda4 EXTENDED
[*]   - sda5 - NTFS - 20 GB (for my work files)
[*]   - sda6 - FAT32 - ~40 GB - for sharing with Windows (my music, movies...)
[/LIST]
Unfortunately this is not possible because on boot windows keep changing the drive letter of the FAT32 partition to C: and, as a consequence, gave me a lot of problems booting ('cause it assumes C: to be the one with the OS - stupid windows!!!)

So, all my problems started because of that and now I have the same scheme but, instead of a FAT32, a NTFS partition.

Does anyone knows if it is possible to «fool» windows and have it  keeping the drive letters the way we want?

Thanks for any advice or input from you, guys

Zeca

---

