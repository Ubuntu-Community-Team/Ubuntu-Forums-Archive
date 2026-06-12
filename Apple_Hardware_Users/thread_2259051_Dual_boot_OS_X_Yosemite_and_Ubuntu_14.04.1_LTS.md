---
title: "Dual boot OS X Yosemite and Ubuntu 14.04.1 LTS"
date: 2015-01-01
forum: Apple Hardware Users
---

### Post by jhh on 2015-01-01
I have a late 2009 iMac, and I am currently running OS X Yosemite. I am new to Linux, and I would like to install Ubuntu 14.04.1 LTS on my iMac and dual boot. I'm having some issues:

I've been able to successfully install rEFInd, and when I reboot -- I'm able to select OS X, shutdown, restart, etc. With the DVD in the drive, I am not given an option to boot from that drive. After restarting, I forced it to load from the CD/DVD drive and was given the option of running the LiveCD or installing Ubuntu. The installation process says that no other OS is recognized and gives me options to erase everything and install Ubuntu, some others, and lastly "something else."

I went into disk utility and partitioned my HardDrive from 500GB to 400GB (with 100GB free space). 


Any help on how to make this happen would be very appreciated.
Thanks,
Jhh

---

### Post by slickymaster on 2015-01-01
*Moved to the ***Apple Hardware Users*** sub-forum*

---

### Post by jhh on 2015-01-01
any help?

---

### Post by davidchute26 on 2015-01-02
Switch on the Mac holding the option [alt] key, select the CD/DVD drive and let me know if [ubiquity]("https://wiki.ubuntu.com/Ubiquity") then recognises the OS X partition at the stage mentioned above.

Just incase you haven't come across it yet, [the wiki page for Ubuntu/MacBook support]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")

[Edit]
This is [by far the best guide]("https://github.com/aroman/freya-on-a-mac") I can bestow onto you; it uses EFI stub loader which is neat (no GRUB). The steps will work for Ubuntu 14.04.1 (elementaryOS Freya is built on 14.04 LTS).

---

### Post by davidchute26 on 2015-01-02
Also be aware of this [bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192") using the "Something else" option and creating a two partitions "/" (ext4) and "swap" (swap) as shown in the guide is the best way to proceed. I don't think the bug affects 14.04.1 but I've been burnt by this before.

---

### Post by jhh on 2015-01-02
Thanks so much for this -- yesterday when I tried it, it failed to recognize OS X. So instead of the option of installing Ubuntu alongside OS X, I was only given the option of erasing everything and installing Ubuntu, or a couple other options (including other). 

I'll give this a shot now and get back to you.

---

### Post by jhh on 2015-01-02
Still no luck on recognizing OS X -- this is what I'm seeing.
[IMG]http://postimg.org/image/4d3fhm5t3/[/IMG]

---

### Post by jhh on 2015-01-02
@Davidchute26 I'm reading through your best guide link -- he says that you must not have a core 2 duo processor -- instead you need a 64 BIT EFI.


With that information -- any ideas if I can dual boot Ubuntu 14.04.1 LTS and OS X Yosemite with a Core 2 Duo Processor?

---

### Post by este.el.paz on 2015-01-02
> **jhh said:**
> @Davidchute26 I'm reading through your best guide link -- he says that you must not have a core 2 duo processor -- instead you need a 64 BIT EFI.


With that information -- any ideas if I can dual boot Ubuntu 14.04.1 LTS and OS X Yosemite with a Core 2 Duo Processor?

@jhh:

I have had Xubun 14.04 & now LM17 MATE installed on my '10 Core2Duo MBPro . . . that must be important for "Elementary OS" . . . but Ubuntu offers 32 bit and 64bit versions . . . you just have to know which your computer has . . . 64bit units can run 32bit OS, but not vice versa.  There ***may*** be some issue with the installer in terms of system recognition . . . but, did you check the "md5sum" number of your iso to make sure it is correct?  Sometimes if it isn't that can cause issues . . . .  

I've posted many posts here lately about how to install dual and triple boot systems . . . so many times that you should be able to get some ideas.  First thing, with the LiveDVD inserted--did you hold the "c" key while rebooting to get into the Live system??  Or, yes, if rEFInd is installed or not, holding option key should show you the OSX partition, and any other boot-able systems . . . so if OSX isn't showing that is "interesting."  But, if you have booted the installer, it may say "You have multiple systems installed" but not name "OSX" . . . and then ask, what would you like to do?  And, if you have set your 100GB as "Free space" . . . sometimes it will say "Install into largest free space"--that would be the easiest.  Otherwise, right, "something else" . . . I personally have not tried this "GRUB-less" install, for me, when GRUB got messed up in Xubun 14 I couldn't get it to boot linux at all . . . so I set up a small "bios_grub" partition, then the ext4, and then the swap . . . and then it works . . . just have to pass thru a number of windows, including GRUB . . . no big deal.

e.e.p.

---

### Post by jhh on 2015-01-02
@e.e.p.

Thanks for the reply. I have booted now holding "C" and "Control." I am able to boot to the LiveCD and run through Ubuntu; however, when I try to install, it does not recognize that I have any OS currently installed.

I read somewhere about going configuring the partition from the LiveCD environment and then trying to install. I am somewhat new at all this, and hoping to dual boot so I can continue to get more familiar with Linux and programming/tweaking systems and networks.

I appreciate the help so far -- I apologize if some of my questions are very elementary 
jhh

---

### Post by este.el.paz on 2015-01-02
> **jhh said:**
> @e.e.p.

Thanks for the reply. I have booted now holding "C" and "Control." I am able to boot to the LiveCD and run through Ubuntu; however, when I try to install, it does not recognize that I have any OS currently installed.

I read somewhere about going configuring the partition from the LiveCD environment and then trying to install. I am somewhat new at all this, and hoping to dual boot so I can continue to get more familiar with Linux and programming/tweaking systems and networks.

I appreciate the help so far -- I apologize if some of my questions are very elementary 
jhh

@jhh:

There is a learning curve to get linux running on mac, but, it should just be the "c" key with the DVD in the drive . . . "control" is for in linux itself.  You ***could*** configure the partition in the LiveDVD, but if you set it up in OSX you shouldn't need to do that . . . just do it in the installer.  Test question, if you can boot the LiveDVD and use the GUI installer . . . and then choose "something else" . . . the GParted table should open . . . can you see the OSX partition there?  Or something labeled "HFS+"???  And, then, do you see your 100GB space you set aside, should be ***after*** the OSX partitions (sda something) . . . is it labeled as "unallocated" or "free space" or "FAT32"????

If you see OSX there, you could "go back" and try "install alongside" OR continue to use GParted to set up your partitions where you want linux to go--highlight the line and 2x click it to set up your partitions . . . format the "/" partition . . . set up swap . . . possibly the GRUB or not . . . then continue thru the install.  It doesn't always work . . . try again.

Also, I'd suggest trying another flavor and see if it's installer sees OSX . . . like Xubuntu 14 or Lubuntu 14 . . . go with whatever works . . . .

e.e.p.

---

### Post by jhh on 2015-01-02
@e.e.p

Looking at the install, I see the following:
/dev/sda                         
/free space             0 MB  
/dev/sda1 efi          209 MB             209 MB
/dev/sda2 hfs+       400000 MB        156264 MB
/dev/sda3 hfs+       650 MB             529 MB
free space              99248 MB

Device for boot loader installation:
/dev/sda ATA STXXXXX (500.1 GB)
or I can choose
/dev/sda1


So it seems OS X is recognized, but when I go back, it still says there is no OS

---

### Post by davidchute26 on 2015-01-02
Don't worry about OS X not being recognised by ubiquity. Probably because your not using EFI boot loader when you booting from the Live CD. OS X stores its boot loader files in the EFI partition (/dev/sda1 on your system). Anyway using GRUB legacy is no problem at all because rEFInd is able to detect operating system boot loaders across all partitions in the GPT/MBR table. 

So all you need to do is next is create two partitions by selecting "Something else" like so:
"/" (ext4) - 96 GB 
"swap" (swap) - 4 GB
** For now keep the swap partition the same size of as your RAM in GB. Here I've just assumed you have 4 GB of RAM, just adjust the partition sizes to suit your needs.

Your partitioning table will look similar to the below:
/dev/sda  
/free space 0 MB  
/dev/sda1 efi 209 MB 209 MB
/dev/sda2 hfs+ 400000 MB 156264 MB
/dev/sda3 hfs+ 650 MB 529 MB
/dev/sda4 ext4 96 GB
/dev/sda5 swap 4 GB

Click next and run through the remaining steps in the installer, selecting YES to the install GRUB into root partition pop up thingy at the end. When you reboot you will see two icons, one for OS X and another for Ubuntu. That's it. 

If you have any questions grab me on IRC channel (#ubuntu) nickname is high_fiver.

---

