---
title: "Installing XP after Installed Ubuntu &amp; other"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by sim085 on 2006-07-17
Hello,

I have installed Ubuntu on a drive where previously I had only Windows XP.  I used the portioning tool that comes with the Ubuntu Installation and all worked as a charm.  When I restarted I had the options to either load Ubuntu , Ubuntu Safe Mode, Ubuntu Kernel, Other Operations System, and Windows XP.  

My first question is whether there is a way to custom this screen (boot up screen)?

Now I was planning to format the partition where I have Windows XP to re-install it.  Should I expect any problems?  Also would my boot-up screen be replaced with the one created by the Window XP?

Regards,
Sim085

---

### Post by cotcot on 2006-07-17
You can edit the grub screen. It is the file /boot/grub/menu.lst. You can find in the grub manual [http://www.gnu.org/software/grub/manual/grub.html#Interface]("http://www.gnu.org/software/grub/manual/grub.html#Interface")

You can re-install XP. It will indeed replace the grub bootloader. So you will have to re-install the grub bootloader too. This is not difficult. Here is one of the possibilities : [http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub")

---

### Post by Thenotsowyzewun on 2006-07-17
Well you've got several options here, you could:
* Dual Boot
* use [WINE]("https://help.ubuntu.com/community/Wine") to run Windows Programs on Linux
* use [VMWare Player]("http://www.vmware.com/products/player/") or [VMTS]("http://www.vmts.net/article/selfp2v.htm") to run Windows within Linux (or QEMU, there's an excellent guide [here]("http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html"))
* You can even run Linux on Windows, using [VMWare Player]("http://www.vmware.com/products/player/") or [Microsoft Virtual Server]("http://www.microsoft.com/windowsserversystem/virtualserver/default.mspx") (both free, the former is better)

If you'd like to stick with the dual-boot option, the questions been asked before [here]("http://ubuntuforums.org/archive/index.php/t-22537.html") (so you don't have to wait for replies :) ).

EDIT: Just noticed [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") on that thread - Recovering Ubuntu after Installing Windows, from the Ubuntu Community Documentation :).

---

### Post by sim085 on 2006-07-17
Well I am planning to have several Virtual Machines having different versions of linux installed on them, which I plan to use for testing portability of my applications.  However that is a future project :)

At the moment I just wish to make a dual-boot system.  If I let the bootloader set by XP, will I have the option to load Ubuntu?

Regards & Thanks,
Sim085

---

### Post by Thenotsowyzewun on 2006-07-17
AFAIK there's no way to add a Linux option to Microsoft's bootloader, wouldn't be the first time I've been proved wrong though!
GRUB's fine though, the link at the bottom of the above post explains how to fix it after Windows installation :).

---

### Post by sim085 on 2006-07-17
Yes I am reading it at this moment :) However I read that I would need the alternate CD (which I do not think I have).

However I am also reading that it is possible to backup the MBR.  Could I then load from the live CD, and then use the terminal to place it back?  or I would be playing with fire?

regards,
sim085

---

### Post by Thenotsowyzewun on 2006-07-17
Haven't read the guide myself TBH, I'd recommend burning the alternate disc if you've got that option.
You could try reinstating the MBR via terminal, I'll go find some exact instructions (if there are any!).

OK, no need for a backup, or the alternative disc, courtesy of one Michael Manning, [here]("http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/") :) - see the first comment.

EDIT: Not sure if this'll let you boot into Windows without reconfiguring GRUB. The instructions to do that are [here]("http://wiki.linuxquestions.org/wiki/GRUB#Booting_Windows.2FDOS") (although I'm intrigued to learn how Microsoft's MBR can support Linux booting :D).

---

### Post by Apple 101 on 2006-07-17
Yes, you can boot Linux from Microsoft's MBR (technically).  Wait till I find the instructions...

---

### Post by Apple 101 on 2006-07-17
1. Install GRUB to a floppy disk.
2. In Windows use dd (DD for Windows) from the command prompt to create the GRUB boot file.

Use: *dd bs=512 count=1 if=\\?\Device\Floppy0 of=C:\ubuntu.lnx*

This will automatically place the file in C:\
3. Start --> Run --> notepad C:\boot.ini
4. Add in C:\ubuntu.lnx="Ubuntu Linux 6.06" under [operating systems] and Save.

That will load Ubuntu from the Windows XP boot loader.

---

### Post by sim085 on 2006-07-17
Thanks to all, this eveing I will try to format my XP partition install it again, and update my MBR so that my Ubuntu is visible again :)

thanks to all for the comments :)

Best Regards,
Sim085

---

