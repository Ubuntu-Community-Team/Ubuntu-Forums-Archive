---
title: "Intermittent GRUB Error 21 on two-drive dual-boot system"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by wwalkersd on 2007-12-03
I recently installed Gutsy Gibbon (7.10) on my token x86 system (I'm mostly a Mac user), an eMachines T3114 (AMD Sempron 3100+, MSI 7142 mother board with VIA chipsets).  This system was only a Windows XP system prior to this install.  Wanting to have dual boot, but also wanting to play it safe, I stuffed a spare drive 250 GB in the machine.  Against better advice I found later, I left the original Windows XP 80 GB drive as the Master and configured the new drive as Slave.  Possibly of note is that, since the machine only had 256 MB of RAM (since upgraded to 1.2 GB), I was unable to use the Live CD installer and had to use the alternate install.

I formatted the new drive with three partitions, /, /home, and swap.  IIRC, / is 20 GB, swap is 4 GB, and /home has the rest of the 250 GB drive.  And of course the install put Grub in (I presume) the MBR of the Windows drive.

More often than not, when I boot this system, Grub gives me error 21.  If I then reboot via the three-fingered salute (Ctrl-Alt-Del), Grub comes up normally and lets me choose a system, and Ubuntu runs just fine.  I'm guessing that at initial boot time it can't see the second drive for some reason.  Maybe the 250 just takes longer to spin up than the 80?  I dunno.  Any ideas?

---

### Post by speed145a on 2007-12-03
not exactly sure of your situation but remember:

some parts of grub are installed on each of your drives.  so if you change the boot order either in BIOS or adding/removing drives this will impact your ability to boot.

try doing whatever it is you do to get into ubuntu and reinstalling grub.

---

### Post by wwalkersd on 2007-12-03
> **speed145a said:**
> not exactly sure of your situation but remember:

some parts of grub are installed on each of your drives.  so if you change the boot order either in BIOS or adding/removing drives this will impact your ability to boot.

try doing whatever it is you do to get into ubuntu and reinstalling grub.

Can I reinstall grub from my running system?  How do I do that?  Or do I have to boot from the alt install disk again?

---

### Post by Duck2006 on 2007-12-03
This may help

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

The other thing you may do it edit your /boot/grub/menu.lst and remove the line that has

savedefault

---

### Post by wwalkersd on 2007-12-03
> **Duck2006 said:**
> This may help

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

The other thing you may do it edit your /boot/grub/menu.lst and remove the line that has

savedefault

Thanks.  Um, what does removing "savedefault" do, exactly?

---

### Post by Duck2006 on 2007-12-03
> **wwalkersd said:**
> Thanks.  Um, what does removing "savedefault" do, exactly?

If you have savedefault line in your menu.lst, edit your menu.lst

sudo gksudo gedit /boot/grub/menu.lst

and remove the line.

---

### Post by wwalkersd on 2007-12-03
> **Duck2006 said:**
> If you have savedefault line in your menu.lst, edit your menu.lst

sudo gksudo gedit /boot/grub/menu.lst

and remove the line.

OK, thanks, now I know exactly how to go about removing it.  But my question was, what does it do?  What does "savedefault" mean, and what is the effect of removing it?  What I'm saying is, I'd like to understand what I'm doing and why I'm doing it, rather than just cookbooking it.

---

### Post by Duck2006 on 2007-12-03
This is the grub manual

[http://www.gnu.org/software/grub/manual/grub.html#savedefault](http://www.gnu.org/software/grub/manual/grub.html#savedefault)

---

### Post by wwalkersd on 2007-12-03
> **Duck2006 said:**
> This is the grub manual

[http://www.gnu.org/software/grub/manual/grub.html#savedefault](http://www.gnu.org/software/grub/manual/grub.html#savedefault)

Great resource, thanks!  But having read it, I don't understand what effect it might have on my problem.  Isn't it just telling grub to boot into the same system I last booted into if I don't choose from the menu in time?

---

### Post by Duck2006 on 2007-12-03
Did you reinstall grub?
If so didit work ok for you?

---

### Post by wwalkersd on 2007-12-03
> **Duck2006 said:**
> Did you reinstall grub?
If so didit work ok for you?

Yup, I just got a chance to reinstall grub.  A couple of things:

1) the commands from thehowtogeek aren't correct for Gutsy, apparently.  The "setup (hd0)" command produced an error.  Having tried that, and waiting and waiting on the Live CD (which insisted on displaying its menu bar off the top of my screen, which confused me for a while), I figured that since I was installing on another drive, there was nothing magic about doing it from the Live CD, so I'd just do it from my live system.  Again, the commands didn't work.  But I did some snooping around and found a script called grub-install, and gave that a try (there's even a man page for it!).  It completed correctly.  However, I still get Error 21 on initial boot.  I also tried removing the "savedefault" entries in /boot/grub/menu.lst, which were only present on the XP main partition and the XP recovery partition, not on any Ubuntu partitions.  I gather they wouldn't do anything, anyway, since the file also contains the command "default 0".  In any event, this also didn't fix the problem.

Other ideas?  It's not a huge deal, as long as I'm only using the system interactively.

---

### Post by wwalkersd on 2007-12-04
Update:  I got the intstructions from How-to Geek to work after reading the grub manual you linked (thanks again!).  Since I have Ubuntu on my second hard disk, for me the commands were:

root (hd1,0)
setup (hd0)

The bad news is it didn't make any difference.  I still get error 21 on initial power-on.

---

### Post by wwalkersd on 2008-01-29
Well, it looks like I've finally solved this problem.  I made my Ubuntu drive the Master and made the Windows drive the slave, installed Grub on the new master, and all is hunky-dory.  I think.  Except I think I need to reinstall the Windows MBR on the Windows drive.  Perhaps this is the wrong place to ask, but how do I do that?

---

