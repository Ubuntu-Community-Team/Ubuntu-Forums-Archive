---
title: "Dual Boot with Windows"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by pgn674 on 2006-09-19
Alright, I'm an advanced Windows user, and want to give Linux a try. I've heard good things about Ubuntu, and my professor recommends it for my class too.

First, a back ground story: What I had was 3 hard drives, each with 1 partition, all NTFS. Windows installed onto the first hard drive, the other two used for data storage. I cleared out the 3rd hard drive (a Secondary Master), and installed Ubuntu on it. I choose the custom partition option during install, and had it set up a 15GB partition (ext3 I think, whatever's default), and 1GB swap file, and leave the rest unformatted as a partition. After a successful install, I restarted the computer and got the choices menu showing Ubuntu, Windows XP, and some diagnostic Ubuntu modes startups. Selecting the Ubuntu one, it booted up fine. Happy days :)

Then I restarted, choose Windows on that menu, and noticed that Windows saw the 3rd hard drive as unknown size and unformulated. So I booted into my Windows XP Pro CD, started a Windows install on the unformatted partition on my 3rd hard drive (the CD could see the partitions OK), and stopped the install once the partition was formatted for NTFS. I booted back into Windows, noticing that I didn't get the Ubuntu OS select screen, and Windows saw the NTFS partition on the 3rd hard drive fine. Size and everything is correct, Windows just doesn't see the Ubuntu or swap partitions.

Now the bad part: I can't boot into Ubuntu. There is no more Ubuntu OS selection screen. The Windows OS selection screen (hit F8 ) has only Windows XP. Trying to boot right off the 3rd hard drive is no good: BIOS says it's an improper boot device (standard non-bootable message I believe). So, what happened, and how do I fix it?

I've done some searching on these forums and Google, but nothing seems to fit my current unique situation. If need be, I'm OK with re-installing Ubuntu on that partition I made for it.

My guess is, when Ubuntu installed, it changed the section first scanned on the Primary Master drive (my Windows install) by the BIOS, and put in a different menu, remembering to include the OS that was already referenced there. Then, when I booted into Windows, Windows decided it didn't like that, and over writ it back to its own default OS choices menu.

So, any recommendations? Something about lino, grub, mbr, boot.ini, /boot, and ntldr I bet :)

Oh, and if possible, I'd like to avoid resizing my Windows partition on my Primary Master.

---

### Post by deadgobby on 2006-09-19
Welcome to Linux and remember that it is not microstuff. 1st off windows hates any other o/s except windoz. 
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29)
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
[http://pcmech.com/show/os/917/](http://pcmech.com/show/os/917/)
 Enjoy the freedom of a world with out M/S.:D

---

### Post by confused57 on 2006-09-19
You need this for Windows to recognize Linux(ext2 or ext3 partitions):
[http://www.fs-driver.org/](http://www.fs-driver.org/)

You can reinstall grub using the live cd:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

When you first installed Ubuntu to your 3rd hard drive, grub was probably installed to the mbr on the 1st hard drive.  When you reinstalled Windows, it probably overwrote grub...you could choose to reinstall grub to the 1st hard drive mbr, using the live cd method(probably the better choice)...or install grub to the 3rd hard drive (hd2) and boot it from bios.
I'm no expert, but that's my take on what's happened.

---

### Post by xhaan on 2006-09-19
> **pgn674 said:**
> Alright, I'm an advanced Windows user, and want to give Linux a try. I've heard good things about Ubuntu, and my professor recommends it for my class too.

First, a back ground story: What I had was 3 hard drives, each with 1 partition, all NTFS. Windows installed onto the first hard drive, the other two used for data storage. I cleared out the 3rd hard drive (a Secondary Master), and installed Ubuntu on it. I choose the custom partition option during install, and had it set up a 15GB partition (ext3 I think, whatever's default), and 1GB swap file, and leave the rest unformatted as a partition. After a successful install, I restarted the computer and got the choices menu showing Ubuntu, Windows XP, and some diagnostic Ubuntu modes startups. Selecting the Ubuntu one, it booted up fine. Happy days :)

Then I restarted, choose Windows on that menu, and noticed that Windows saw the 3rd hard drive as unknown size and unformulated. So I booted into my Windows XP Pro CD, started a Windows install on the unformatted partition on my 3rd hard drive (the CD could see the partitions OK), and stopped the install once the partition was formatted for NTFS. I booted back into Windows, noticing that I didn't get the Ubuntu OS select screen, and Windows saw the NTFS partition on the 3rd hard drive fine. Size and everything is correct, Windows just doesn't see the Ubuntu or swap partitions.

Now the bad part: I can't boot into Ubuntu. There is no more Ubuntu OS selection screen. The Windows OS selection screen (hit F8 ) has only Windows XP. Trying to boot right off the 3rd hard drive is no good: BIOS says it's an improper boot device (standard non-bootable message I believe). So, what happened, and how do I fix it?

I've done some searching on these forums and Google, but nothing seems to fit my current unique situation. If need be, I'm OK with re-installing Ubuntu on that partition I made for it.

My guess is, when Ubuntu installed, it changed the section first scanned on the Primary Master drive (my Windows install) by the BIOS, and put in a different menu, remembering to include the OS that was already referenced there. Then, when I booted into Windows, Windows decided it didn't like that, and over writ it back to its own default OS choices menu.

So, any recommendations? Something about lino, grub, mbr, boot.ini, /boot, and ntldr I bet :)

Oh, and if possible, I'd like to avoid resizing my Windows partition on my Primary Master.


Yup, you're right. Windows likes to be the only operating system on a computer, so when you install it, it overwrites the Master Boot Record.
Even though you didn't completely reinstall Windows, this is likely what it did just by running the installer.

You could try this:
[RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by whitewizardcoder on 2006-09-19
The reason Windows didn't see your Ubuntu (ext3) partition is because, as deadgobby said, Windows doesn't like any other operating systems.  This means it will also not see any partitions other than Windows partitions (FAT, NTFS).  The only way to access the ext3 partition in Windows is to get an ext3 driver program.

Now for some bad news.  When you reformatted the third hard drive using NTFS, you wiped out the Ubuntu install.  Currently, Ubuntu can only be installed on ext2 or a derivative (e.g. ext3).

The Windows XP installer automatically overwrites the Master Boot Record, which is a portion of the hard drive that boots up first.  When you installed Ubuntu, grub (a bootloader) stuck a small piece of code in there to tell it to show the different boot options.  Windows Master Boot Record only tells the hard drive to boot into Windows, overriding grub's MBR.

So, you're looking at a fresh Ubuntu install on your third hard drive.  And don't pay attention to what Windows tells you about the hard drive.  If its not a Windows-friendly partition, it will want you to reformat (which you don't want to do).

Good luck!

-WhiteWizardCoder

---

### Post by pgn674 on 2006-09-19
> **whitewizardcoder said:**
> Now for some bad news.  When you reformatted the third hard drive using NTFS, you wiped out the Ubuntu install.
-WhiteWizardCoder

Actually, I might not have been clear on that. I told Windows to only format the unformatted partition, so it didn't touch Ubuntu. I got a driver thingy to let Windows see and read ext* formattings, and I can see my Ubuntu installation all nice and pristine from Windows Explorer :)

So now, I'm going to try to reinstall Grub into the MBR as directed here:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by confused57 on 2006-09-19
You may have to add your entry to boot Windows, after reinstalling grub:

```
title     Windows XP
root      (hd0,0)
savedefault
makeactive
chainloader +1
```

Something like the above entry.

---

### Post by pgn674 on 2006-09-19
HAPPINESS!

It works :) It looks like when I used the Windows installer to format the partition into NTFS, it got as far as redoing the master boot record before I stopped it. And nope, I only needed to re-install GRUB, there was no cleanup to do afterwords.

For those reading this thread in the future, I used [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) to solve my problem.

---

