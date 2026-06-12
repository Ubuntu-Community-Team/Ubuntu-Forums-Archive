---
title: "Is Ubuntu 32 and 64 (and vista) multi-boot possible? How should I partition?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by Baelari on 2008-03-01
[SIZE="1"] Lenovo X61 tablet is compatible with Ubuntu, right?[/SIZE]
      
[LIST]

[*]Is 4GB of RAM a significant waste for a 32 bit OS? 


[*]Is it possible to have both a 32 and 64 bit Ubuntu on the same disk?


[*]Is there a way for x64 to use programs from the 32 bit OS, but keep x64 things to itself?[SIZE="1"] (i.e. do I have to install a duplicate for 64?)[/SIZE]


[*]What would be the best way to partition the drive/What file systems would be best?[SIZE="1"] (I tend to break things I don't know how to fix, and just reinstall. Important things go elsewhere.)[/SIZE]


[*]Which pairs of numbers do I put in the GRUB thing?
[/LIST]

I know practically nothing about how Linux runs, or how computers actually work, but would like to learn. Any advice is appreciated.

---

### Post by hhhhhx on 2008-03-01
> **Baelari said:**
> [SIZE=1] Lenovo X61 tablet is compatible with Ubuntu, right?[/SIZE]
[LIST]
[*]Is 4GB of RAM a significant waste for a 32 bit OS?
[*]Is it possible to have both a 32 and 64 bit Ubuntu on the same disk?
[*]Is there a way for x64 to use programs from the 32 bit OS, but keep x64 things to itself?[SIZE=1] (i.e. do I have to install a duplicate for 64?)[/SIZE]
[*]What would be the best way to partition the drive/What file systems would be best?[SIZE=1] (I tend to break things I don't know how to fix, and just reinstall. Important things go elsewhere.)[/SIZE]
[*]Which pairs of numbers do I put in the GRUB thing?[/LIST]I know practically nothing about how Linux runs, or how computers actually work, but would like to learn. Any advice is appreciated.
not realy
 
yes
 
yes, but there realy slow, also all the programs in the repositories have 64 bit versions
 
last 2 i dont know

---

### Post by John.Michael.Kane on 2008-03-01
> **Baelari said:**
> [SIZE="1"] Lenovo X61 tablet is compatible with Ubuntu, right?[/SIZE]

According to this Ubuntu Gusty 7.10 should work.
[http://www.linlap.com/wiki/IBM-Lenovo+Thinkpad+X61](http://www.linlap.com/wiki/IBM-Lenovo+Thinkpad+X61)
      
[LIST]

> **Baelari said:**
> [*]Is 4GB of RAM a significant waste for a 32 bit OS? 
No, you might have an issue though regarding the ability of 32bit addressing the full amount of ram.


> **Baelari said:**
> [*]Is it possible to have both a 32 and 64 bit Ubuntu on the same disk?
Yes, install your 32bit version first. followed by the 64bit version. you can this using the alternate/text based cd's 


> **Baelari said:**
> [*]Is there a way for x64 to use programs from the 32 bit OS, but keep x64 things to itself?[SIZE="1"] (i.e. do I have to install a duplicate for 64?)[/SIZE]
Yes, in theory you can run 32bit base Linux programs under 64it.

See this thread for information [http://ubuntuforums.org/showthread.php?t=474790&highlight=get+libs](http://ubuntuforums.org/showthread.php?t=474790&highlight=get+libs)

Side note: Most programs in the Ubuntu repo's have native 64bit versions.

> **Baelari said:**
> [*]What would be the best way to partition the drive/What file systems would be best?[SIZE="1"] (I tend to break things I don't know how to fix, and just reinstall. Important things go elsewhere.)[/SIZE]

Most users run ext3, and a configuration like this.
/root
/home
swap

Note: There are other configurations,however, The above is considered standard.

> **Baelari said:**
> [*]Which pairs of numbers do I put in the GRUB thing?
[/LIST]
More information would be needed from you, as to what you are trying to ask.

---

### Post by Baelari on 2008-03-01
[LIST]
[*]what is the purpose of /root and /home? and how big should I make them?
[/LIST]

It was something at the end of the file that made GRUB recognize other OS's, looks like coordinates (0,1) 
no clue what they mean, I just guess sequentially until it shows what I want when I restart.

---

### Post by Kevbert on 2008-03-01
Multiboot of all three operating systems is possible.  I'm using Ubuntu 64, 32 bit on one SATA drive and Win XP on another.
You'll need to install Vista first (NTFS preferred).
Next install Ubuntu 32 bit, then 64 bit last.
Running 32 bit programs on 64 bit Ubuntu can be a problem as the program may complain or you may have problems with installing it (e.g. flash plug-ins), but there are ways to get around this.
Grub will sort itself out via the Ubuntu installs.  The only problem is that you'll need to distinguish between the 32 bit and 64 bit Ubuntu versions.  As the 64 bit Ubuntu is the last to install, it will be the default OS to boot-up, But will look the same as the 32 bit version from the menu.  You can edit the boot file menu.lst to change this.

---

### Post by Baelari on 2008-03-01
[LIST]
[*]oh, and do I make separate /home and /root for both 32 and 64?
[/LIST]

---

### Post by Baelari on 2008-03-01
[LIST]
[*]Is there an easy way to see what OS corresponds to what number for the menu.lst file?
[/LIST]
Grub throws up a ton of menu items and skips the preinstalled vista things whenever it gets messed up on this computer. Last time I fixed it, it seemed like it was a random number.

---

### Post by Dr. Koncar on 2008-03-03
Scenario: You want the simplest way to dual-boot Vista and Linux. You've already installed Windows Vista and now want to dual-boot it with Ubuntu 7.04
Summary of tutorial: This is an updated tutorial - we previously used Ubuntu 6.10 and then modified the GRUB bootloader to force Ubuntu to recognise the Vista partition. In this tutorial, we'll use Ubuntu 7.04 which does a much better job in interacting with Vista. We'll use the Vista management tools to resize the main partition and install Ubuntu into the freed space.
This tutorial has been tested on a VMWare Workstation 6 machine and an ASUS P5AD2-based Intel system with 2GB RAM and an 80GB Seagate SATA drive.
Get started

Boot into Windows Vista and go into Disk Management - right-click My Computer, Manage, Disk Management.

Vista Disk Management
 
 
Right-click on the main Vista partition and select Shrink Volume

Vista Disk Management - Shrink Volume

 
The Shrink tool will assess how much space can be freed up.

Vista Disk Management - Shrink Volume 2

As a rule of thumb Shrink will reduce the main system partition by about 50%. As long as the partition is big enough to begin with (at least 10GB) it should accommodate both operating systems.
Select Shrink and the tool will reduce the volume of the primary partition, leaving the rest of the disk free as unpartitioned space.

Vista Disk Management - Shrink Volume 3

 
Once that's done, shut down the Vista machine.
 
Install Ubuntu

You'll need the latest desktop ISO of Ubuntu (7.04). You can choose a list of download mirrors from the Ubuntu website, or use this link from Planetmirror. Download the ISO and burn it to CD to create an Ubuntu Live CD.
Boot the Vista machine from the Live CD and select "Start or install Ubuntu".

Vista & Ubuntu - Install Ubuntu

 
Once the Live CD has loaded, double-click the Install icon on the desktop to start the installation process.
On the Welcome screen, choose your language and select Forward.

Vista & Ubuntu - Install Ubuntu - Language
On the "Where are you" (timezone) page, select your location and then Forward.

Vista & Ubuntu - Install Ubuntu - Timezone
 
On the next screen, choose the appropriate keyboard layout and then Forward.

Vista & Ubuntu - Install Ubuntu - Keyboard

 
Ubuntu will then load the disk partitioner to determine where it's going to be installed. Choose "Manual - use the largest continuous free space". This will automatically select the unpartitioned space we created earlier using the Shrink tool. Click Forward.

Vista & Ubuntu - Install Ubuntu - Disk Partitioner

On the Migrate Documents and Settings screen, if Ubuntu finds any user accounts to migrate, feel free to import it from Vista to Ubuntu. If it doesn't find any, obviously this isn't an option. Click Forward.

Vista & Ubuntu - Install Ubuntu - Migrate

 
On the "Who are you?" screen, enter your username and password details, then click Forward.

Vista & Ubuntu - Install Ubuntu - User Details

 
On the "Ready to install" screen, you'll see that Ubuntu now has enough information to commence the installation. In the summary under Migrate Assistant, it should say "Windows Vista/Longhorn (loader)". This means that regardless of whether Ubuntu found any user account to migrate, it certainly knows that Windows Vista is installed on the other partition and is aware of it. Click Install.

Vista & Ubuntu - Install Ubuntu - Install

 
See the install through and then let it boot into Ubuntu.
When the install is complete the system will reboot. When the GRUB boot menu is displayed, have a look at the last entry in the list.

Vista & Ubuntu - GRUB Bootloader

After the Ubuntu boot options, there will be an entry &#8220;Other operating systems&#8221; and beneath that "Windows Vista/Longhorn loader&#8221;. By default Ubuntu will load itself after 10 seconds, but you can select the Vista option and Vista will boot normally.
 
Configure GRUB

If you want to modify how GRUB handles the new dualbooting environment, you need to edit the boot menu. Boot into Ubuntu and open up a Terminal window (Applications, Accessories, Terminal), and type in:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
and enter your root password when asked - this makes a backup of the GRUB menu file just in case things go wrong.
Next, type in:
sudo gedit /boot/grub/menu.lst

Dualboot - Configure Boot Menu

 
This opens up the boot menu as a text file in gedit.

Dualboot - Boot Options

 
There are loads of options you can change, but only a couple that you&#8217;re likely to be interested in. The default boot entry is defined by the &#8220;default&#8221; value.
The default value is 0, which means that the first entry in the list (which is Ubuntu) always gets loaded.
If you want to make it so that Windows Vista loads by default, change the value to 4, as Vista is the fifth item in the list (the numbering system starts at 0 and "Other operating systems" counts as a line).
The other way to load Windows Vista by default is to change the value for &#8220;default&#8221; from a numerical value to &#8220;saved&#8221;. Then, GRUB will load whichever boot entry has been marked with &#8220;savedefault&#8221;.
If you scroll down the list and have a look at the entries, you&#8217;ll notice that both the main Ubuntu entry and Windows Vista have been marked with &#8220;savedefault&#8221;. Remove the value for Ubuntu and Windows Vista will launch by default.
It's also worthwhile changing the description of the Vista entry from "Windows Vista/Longhorn (loader" to just "Windows Vista".
You can also increase the boot menu timeout &#8211; just change the value for &#8220;timeout&#8221;. You can also hide the GRUB boot menu by removing the hash in front of &#8220;hiddenmenu&#8221;. Save and exit gedit to keep any changes.
If instead of GRUB you want Vista's bootloader to be in charge, load up the Vista installation and install EasyBCD. Go to &#8220;Manage Bootloader&#8221;, then &#8220;Reinstall the Vista Bootloader&#8221;, an GRUB is overwritten. You can then configure the Vista bootloader to add Linux to the boot menu.
Source: APC Mag
I know this is the way to boot Vista and Ubuntu. Vista installed first. I guess that you log in to Vista and create another partition and boot up 64 bit ubuntu and select install to most free space.
Hope this helps!!

---

### Post by Computer Guru on 2008-03-05
Perhaps this pictorial (made for EasyBCD, Vista, and Ubuntu specifically) is a tad easier to follow:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by Baelari on 2008-03-05
I'm not necessarily worried about the simplest way to do things, but the most convenient later on.

After looking at it a bit more, maybe the question I should be asking is, when I get my OSs set up, preferred programs/packages installed, and settings set, How could I partition and make a backup to the same disk? I'm not worried about the disk being fried, but the convenience of wiping away all the things I have broken, or just tidying up after putting a bunch of junk on the disk.

Backing up to an SD card would be ok, or to my iPod would be ok as long as it doesn't lose functionality to play music. Clunky external HD is my very last choice.

I have to do everything without an optical or floppy drive, btw.

---

