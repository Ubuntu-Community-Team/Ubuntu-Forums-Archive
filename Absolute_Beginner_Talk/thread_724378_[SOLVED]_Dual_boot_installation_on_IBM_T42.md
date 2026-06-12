---
title: "[SOLVED] Dual boot installation on IBM T42"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by wiseloki on 2008-03-14
My installation won't boot

I am moderately competent in using XP and know almost zero about unix/Linux/Ubuntu.

I have been playing with Ubuntu 7.10 (Gutsy Gibbon) off the CD and finally decided to install on an IBM T42 laptop as a dual-boot with XP. I want a secure machine for carefree browsing. The plan was to make sure all aspects of the T42 work in Linux (being able to check them in XP if required) then eventually dump XP and free up the disk space - it's only got a 40GB HDD.

I read some of the forums and Ubuntu information and decided to have a separate root ('/'), so used the partitions utility on the CD to resize the XP NTFS partition to 10GB (files  actually use 7.7GB), set up a 4MB swap partition (laptop has 1MB RAM, and I may take it to 2MB), created a root ('/') of 4GB and '/home' of the rest of the HDD, about 26GB (I tried to create an additional 4GB FAT32 partition for some common files, but any partition after the fourth was coming up unusable, no matter which order I created them in)

I then installed.

I restarted the machine and got the boot table (GRUB?) to select the OS I wanted.

First I tried XP and got ScanDisk (I guessed that this was a response to the partition resize) - after it had scanned, XP started OK.

Then I tried Ubuntu - and after a couple of lines of text the screen stayed blank with the HDD twitching occasionally. No boot, so I crashed it with the power button.

I tried the recovery mode, and the screen scrolled through the various commands, finally stopping after:

*Mounting local file systems....[OK]
*Activating swapfile swap...[OK]
$Mounting securityfs on /sys/kernel/security: done.
Loading AppArmor profiles : done
*Checking minimum space in /tmp...[OK]
*Configuring network interfaces....[OK]
*Setting up console font and keymap...[OK]
root@pvs-ibm:~#_


And there it sits. It looks like it's awaiting a command, which implies there's something wrong with the boot. The only way out is to crash it.

Any ideas? Assistance gratefully received

---

### Post by LinuxD on 2008-03-14
Firstly, Welcome to Ubuntu!

> **wiseloki said:**
>  Then I tried Ubuntu - and after a couple of lines of text the screen stayed blank with the HDD twitching occasionally. No boot, so I crashed it with the power button. 
Secondly, Would it be possible to know what these lines said? Though I'm assuming they were likely messages from the boot-up, it may be useful if they were indicating an error of sorts.


> **wiseloki said:**
> I read some of the forums and Ubuntu information and decided to have a separate root ('/'), so used the partitions utility on the CD to resize the XP NTFS partition to 10GB (files  actually use 7.7GB), set up a 4MB swap partition (laptop has 1MB RAM, and I may take it to 2MB), created a root ('/') of 4GB and '/home' of the rest of the HDD, about 26GB
Personally, I think it may be better to give more space to the root partition since many applications that you are going to install will end up in subfolders of your root directory. I gave my root partition 10GB which has been more than enough even with all my applications and games installed. Given that 4GB is the absolute minimum that is recommended by the installer for the root partition, I'm wondering whether re-installing Ubuntu with more space for root might help.


> **wiseloki said:**
> (I tried to create an additional 4GB FAT32 partition for some common files, but any partition after the fourth was coming up unusable, no matter which order I created them in)
This is because you can only have up to four "primary" partitions for your disk. when you chose to create a new partition in gparted, you can chose to create "logical" partitions which I believe are a kind of sub-division of a primary partition. Using these, you can get past the 4 partition limit and be able to have your FAT32 partition for transferring files.

As for your prompt in recovery mode, try giving it the "startx" command to see if the GUI was installed properly. we might be able to find out what isn't working from there. Otherwise, you can restart the computer simply by giving it the "reboot" command at the prompt.

This is all I can do for now until I get ahold of my linux stuff at home, hopefully this will help until I can delve farther into it or until someone else comes up with something.

Best of luck!

---

### Post by wiseloki on 2008-03-14
Thanks for the post LinuxD

To go through your advice:

The message that was on the screen was "Starting up..." followed by a message flashed on the screen saying "Loading <something>" but it was too quick to see what was loading.

I tried "startx" and the screen went black, then into tiny black-and-white chequered squares with the mouse pointer as a black 'X'.

I then got a message that "The session is running as a privileged user" and do I want to quit or continue? Continuing gave the Ubuntu music and the brown screen, then there was a message box saying that "User switcher" has quit unexpectedly. If I opted to reload I got the same message; "Don't load" got me to the normal Ubuntu desktop with 2 HDD symbols, one marked sda1 and the other sda4.

I tried to use the partition manager but it only partially worked. 

I couldn't shut down, I just got an box with the option log out. when I did that, I got back to the "root@pvs-ibm:~#_" line on the black screen. So I crashed it with the power button.

I then reinstalled Ubuntu, resizing the /partition to 10GB as you advised. This time I disconnected my Ethernet cable (I'd done the previous installation with an Ethernet connected to my router) and got a warning about not being able to access security updates.

Installation finished and I rebooted in normal mode - same result.

Crashed with power button

Rebooted in recovery mode; this time the screen scrolled with commands being executed to exactly the same point:

.......
*Mounting local file systems....[OK]
*Activating swapfile swap...[OK]
$Mounting securityfs on /sys/kernel/security: done.
Loading AppArmor profiles : done
*Checking minimum space in /tmp...[OK]
*Configuring network interfaces....[OK]
*Setting up console font and keymap...[OK]
root@pvs-ibm:~#_ <flashing cursor>

startx gave exactly the same result.

So no further forward, I'm afraid (except I now have a 10GB root ('/') and correspondingly smaller /home

---

### Post by wiseloki on 2008-03-14
Just as an experiment, I tried another install with the 4 MB swap, the 10 GB NTFS windows and the rest as root (no separate /home)

Same result - no boot and recovery stops at root@pvs-ibm:~#_<blinking cursor>

Before I burnt the imge to CD I checked the download with md5sums and the checksum was OK, and this same CD has already installed Ubuntu on a Dell C840 laptop, the only difference being that the Dell had an XP installation that was 5 years old and had gone a bit flaky, so I allowed Ubuntu to take the whole partition (top option on the installer).

Anyone any ideas how I can get this install to work? I don't really want to install into one partition on this machine, and all the reading I've done indicates I shouldn't have to.

---

### Post by LinuxD on 2008-03-17
Sorry about the late reply, for some reason my e-mail neglected to inform me that the thread was replied to.

Sorry to hear it still isn't working... from the description I'm wondering if there isn't something wonky going on with the GUI... Once again I'm checking this from the lab at my university so I'll post again shortly with a command that should make it easier for you to post the kernel log to see what's going on (instead of writing it all down verbatim :) )...

---

### Post by spiderbatdad on 2008-03-17
Perhaps stop "crashing the boot" with the power button. Ubuntu can take several minutes to boot with an improperly configured usplash.conf. This is an easy fix. Allow your system as much time as it needs to attempt to configure hardware and screen resolution. Then edit /etc/usplash.conf to x,y=1024x768 respectively. This will not change your system res, only the res used by usplash. After which your system should boot normally.

---

### Post by wiseloki on 2008-03-18
Apologies Guys

I was getting no joy here so I re-posted over in Installation and Upgrades and Peter09 sorted me out.

I forgot to mark this thread solved - apologies. :oops:

There did seem to be some problem with the initial boot where it wouldn't get to the GUI, but changing from the ATI card to Vesa then back to ATI seemed to sort that. Then I had the problem with the splash configuration that spiderbatdad identified, and fixed that from a link that Peter09 gave me telling me how to reconfigure usplash screen resolution.

I now have a dual-boot T42 happily running Ubuntu, with network, wireless and suspend all fully operational.

Thanks for your interest, guys. I'm sure there'll be plenty of opportunity for you to dig me out of the sticky stuff as I start using and learning about Ubuntu.

---

