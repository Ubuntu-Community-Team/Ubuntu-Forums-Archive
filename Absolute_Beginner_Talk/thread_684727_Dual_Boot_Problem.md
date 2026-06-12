---
title: "Dual Boot Problem"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by jfarhou on 2008-02-01
Hi all, I currently have just ubuntu installed on my computer, but i _need_  (not want) to install windows xp as well.  I've tried several times and I seem to just keep messing it up.  Every time I try to install both operating systems I either end up with just Windows, or ubuntu and windows but ubuntu wont load, or just ubuntu and windows cant be loaded.  I currently have 77.6GB of unallocated space on my hard drive upon which I am hoping to install windows.  These are the following steps I have followed upon installing Windows:

> The next step is to reinstate GRUB as the system bootloader. Boot the system using the Ubuntu Live CD.

Go into the GNOME Partition Editor and you can see that the Windows XP Partition is detected as /dev/hda2 and has been marked as the boot partition.

It can actually stay as the boot partition, but as we’re going to reinstall GRUB it makes sense to change this – it doesn’t adversely effect XP.

Right-click the Windows partition and select Manage Flags.

Untick “boot” and select Close.

Then right-click the primary Ubuntu partition (/dev/hda1), select Manage Flags and tick “boot”, then Close. Done.

Now to reinstall GRUB. Open up Terminal (Applications, Accessories, Terminal) and type in:

sudo grub

GRUB - sudo grub

 

This will launch the GRUB application. Now type in:

find /boot/grub/stage1

This will search for where GRUB has been installed, and you should get the result hd(0,0).

Change the active root to this location by typing in:

root (hd0,0)

 

Now we’re going to reinstall GRUB to the MBR rather than the Ubuntu partition.

If we were going to use the Windows XP bootloader then we’d reinstall GRUB to hd(0,0), but as we’re not, type in:

setup (hd0)

GRUB - reinstall grub to MBR

This restores GRUB to the MBR. Type in QUIT and then EXIT to get out of GRUB and Terminal respectively, then reboot the system. Ubuntu will load by default.

 
Modify the Boot Menu

What we need to do now is modify the GRUB boot menu to allow Windows XP to load. Boot the system into Ubuntu and go to Terminal. Type in:

sudo gedit /boot/grub/menu.lst

GRUB - MENU.LST

 

This loads the GRUB menu file (which is basically a text file) within GEdit.

Navigate down to the section which after “## ## End Default Options ##".

These are the individual menu items in the GRUB menu.

Ubuntu &amp; XP - GRUB MenuUbuntu & XP - GRUB Menu

 

To create a new entry, navigate down to the end of the list (although it can go anywhere really) and enter the following lines:

title Windows XP

root (hd0,1)

makeactivechainloader +1

GRUB - Windows XP boot option

 

This places an item in the boot menu to launch Windows XP from its own partition (hd0,1).

If you like, scroll up to the top of MENU.LST and find the line called TIMEOUT.

The numerical value assigned to TIMEOUT dictates how long you’ve got to go into the boot menu (in seconds) before the default boot item loads.

When configuring a dual-/multi-boot system I find it better to increase this value.

 

GRUB - timeout

 

Just above TIMEOUT is DEFAULT. This specifies which boot entry is the default.

The numbering system starts at 0 and counts upwards, so the DEFAULT = 0 means that Ubuntu is always the default entry.

If you want Windows XP to be the default, replace the value.

GRUB - default

 

Save MENU.LST and exit from GEdit, then restart the system.

Hit ESC when prompted to bring up the boot menu, and there’s the newly-created Windows XP entry.

Navigate to this boot item and hit Enter – Windows XP will load.


Only XP doesnt load when I select it from the boot list, instead I get Error 13, and all that can be loaded is Ubuntu.  When I went into my partition editor, it said that my windows partition had errors.  Please can someone just help me use windows and ubuntu in peace?

---

### Post by jan quark on 2008-02-01
the easiest way is to install windows **first**

make a second partition in windows, a blank one

and then install ubuntu as the **second** os, selecting during the installation process
install on biggest continuous free space or something like that

---

### Post by dstew on 2008-02-01
Basically, the steps you listed are correct. As usual, the devil is in the details. For example, in the list of grub commands to boot the Windows system, it says> To create a new entry, navigate down to the end of the list (although it can go anywhere really) and enter the following lines:

title Windows XP

root (hd0,1)

makeactivechainloader +1
Two things: first, the root given may not work for your system. That is, your root might be a different partition from (hd0,1). Second, the statement makeactivechainloader +1 should have a line break between makeactive and chainloader (you probably knew that). Third (OK, there are three things) if Windows is on a disk other than (hd0) you will probably have to use map statements to get it to boot. See the "DOS/Windows" section in the [Gnu grub manual]("http://www.gnu.org/software/grub/manual/grub.html"). I assume that you currently have Ubuntu booting, and have installed Windows on the partition you mentioned, but it is not booting, correct?

---

### Post by Michl on 2008-02-01
As above, the safest way is to install windows first and let it take over the
hard disk.  Then, second, install ubuntu and let ubuntu do the partitioning.
Do not mess with manual partitioning.  Ubuntu will do all the hard work
for you and after rebooting you will have a nice neat Grub menu that
will give you a choice of operating systems.

---

