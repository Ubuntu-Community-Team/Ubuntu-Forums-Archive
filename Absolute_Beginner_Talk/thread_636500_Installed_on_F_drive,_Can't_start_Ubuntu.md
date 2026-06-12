---
title: "Installed on F drive, Can't start Ubuntu"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by ottawaexec on 2007-12-09
This problem seems to be addressed in numerous threads. I originally "replied" to the most appropriate. However I think doing this does not give my search for help much visibility, so I am reposting as a new tread.
All is repeated below

"" Originally Posted by w4ett  View Post
Exactly the same installation that I have....2 drives give you much more flexibility and peace of mind. Load grub on the master and Ubuntu on you slave drive, this will save any problems with re-partitiong. The live CD gparted makes this a breeze.
This sounds like the answer to my problem.""

My (Ottawaexec) post
Just got Ubuntu 7.10 at an OCLUG meeting this past week and installed it to an F drive.
Using an older computer that has only a 4 GB C drive; the newer F drive has 160 GB
During installation, I was offered choices as to installation site and partitioning. I picked my larger F drive, with no partition. I was informed that all info and programs would be errased, but I guess that only applies to the drive chosen.
My C drive has windows 2000 and applications.
When I start up, I just get Windows, can't get Ubuntu.
Your comment seeems to say I have to copy a file called "grub" to my c drive. is that correct?
I don't care if I lose everything on the c drive as I want this computer dedicated to Linux so that I can give it an honest try.
I have to admit, during the installation I felt good about what I was doing for the first time in over 12 years. Way back then I could build my own menu, use dos commands to do things quickly, etc.. Since then I seem to be constantly fight the programs.

So is "grub" the answer? Or can I physically switch plugs to make my newer drive the c drive?
(As you can see, I have big gaps in my computer knowledge - "A little knowledge can be a dangerous thing"
Thanks for your patience in hearing me out, and for any help.

Ottawaexec
__________________

---

### Post by Moop on 2007-12-09
The problem is that your pc is booting from the wrong hard drive. You need to access the boot order settings in the bios and change the boot order so that F drive boots first. 

That should give you the option of booting Ubuntu or Windows.

---

### Post by Kitsun on 2007-12-09
Firstly there is no such thing as an "F" or "C" drive, thats just the lingo Windows uses to maintain backwards compatibility with DOS, once you get used to Linux you will notice how laughably primitive it is.

Ubuntu should of handled GRUB by itself, but it didn't.

Its possible to manually install GRUB, but I'm not very experienced in that area.

The easiest solution (read: not best) would be to disable the drive that has Windows on it from the BIOS, and just re-enable it when you want to use it, this can be annoying if you dual-boot often, but there is no reason why it shouldn't work.

---

### Post by Dr Small on 2007-12-09
> **Moop said:**
> The problem is that your pc is booting from the wrong hard drive. You need to access the boot order settings in the bios and change the boot order so that F drive boots first. 

That should give you the option of booting Ubuntu or Windows.
+1 That is what I was going to suggest.
It's booting the wrong drive.

---

### Post by ottawaexec on 2007-12-11
> **Dr Small said:**
> +1 That is what I was going to suggest.
It's booting the wrong drive.

Changed the bios so that F drive boots. Didn't work; the computer would not boot up at all.
Checked the drive (C & F) with Windows Explore: It said F was not formatted (yet I had installed all of Ubuntu on it), and, on C, I found the folders Ubuntu>disks>boot>grub, but Windows Explore showed nothing in the folders.
When I start the computer from C drive, Windows asks me to Uninstall Ubuntu.
I am feeling very confused and stupid.
Does Linux format a drive such that windows does not recognize it is formated?
Has Windows somehow automatically erased Ubuntu from drive F?

Please understand this is my first attempt at Linux, and I do not understand the simplest concepts in Linux and Ubuntu.

Appreciate any suggestions.

Ottawaexec

---

### Post by bitterbug on 2007-12-11
*"Does Linux format a drive such that windows does not recognize it is formated?"*

Yes. Unless you have drivers installed in Windows that support the ext2 or ext3 file systems, Windows will not recognize them.

If you boot your Linux cd to a desktop (I'm assuming it's a LiveCD that lets you try the desktop out before installing), then you should be able to see both your 4 gig drive and 160 gig drives, and verify that the 160 now has files on it.

I'm not sure what to do about fixing the Grub though. I've always found the whole boot-loader thing to be a pain in the butt since Windows has never played friendly with them.



P.S. You can get a driver that lets Windows see Linux filesystems here: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by ottawaexec on 2007-12-11
Thanks bitterbug.
I should know about Linux formatting, but I thought I would get into linux via applications, then gradually learn. Instead of asking simple questions that embarrass me, I will try to find a good manual to study for a few weeks.

Now I know I still have Ubuntu installed on F drive. C drive has a subfolder called "grub", but nothing shows up in it (by Windows Explore). So I assume that F doesn't have Grub, and that is why I can't boot up Ubuntu when I direct the Bios to F-drive.
Solution??? Do i reformat C-drive in Linux (not sure how) and eradicate all Windows items on the entire computer (that's OK by me), and then somehow get "grub" reinstalled on C-drive (or F drive)? As I mentioned, C-drive (IBM - DCAA - 34330) is barely 4 gig, so I should keep Ubuntu on F (WDC WD1600JB - 00GVAO). Hope I don't have to reinstall everything over again.
Any thoughts anyone?
I am amazed by the patience of everyone in even considering my problems. Thanks.

Ottawaexec
Your Linux abyssedarian

---

### Post by Martje_001 on 2007-12-11
If you're not afraid of losing data you could install Ubuntu onto (what you call) the C drive. Grub will automaticly be installed.

---

