---
title: "No Grub bootloader. Help!"
date: 2012-10-07
forum: Any Other OS
---

### Post by intelamd on 2012-10-07
I installed Mint 13 Cinnamon today. I already have Windows XP installed. Now the problem is that the grub bootloader does not appear. Instead when I start the PC I see "Frequency out of range - 90 K / 59 HZ" on the monitor and after a while Mint loads. I posted this problem on the Mint forums too but no solution yet. Since Mint is basically Ubuntu and Ubuntu has a very vibrant and cooperative community I am posting my problem here in the hope that some one would help me. So kindly help me.:)

---

### Post by mamamia88 on 2012-10-07
> **intelamd said:**
> I installed Mint 13 Cinnamon today. I already have Windows XP installed. Now the problem is that the grub bootloader does not appear. Instead when I start the PC I see "Frequency out of range - 90 K / 59 HZ" on the monitor and after a while Mint loads. I posted this problem on the Mint forums too but no solution yet. Since Mint is basically Ubuntu and Ubuntu has a very vibrant and cooperative community I am posting my problem here in the hope that some one would help me. So kindly help me.:)

weird maybe try and reinstall grub?  maybe take a look at something called super grub disk [http://community.linuxmint.com/tutorial/view/245](http://community.linuxmint.com/tutorial/view/245)

---

### Post by cipherboy_loc on 2012-10-07
Could you run the boot info script in my signature and post the results in *code* tags? 

**Edit: Disregard my post, Bucky Ball understood the problem better than I did.**

Thanks,
Cipherboy

---

### Post by Bucky Ball on 2012-10-07
If you're talking about the menu at the beginning then hit Shift after the BIOS screen at boot to get a menu.

As for the other issue, are you using any third party graphics drivers or using the open-source default? Looks like it's having problems with your monitor which accounts for the delay.

---

### Post by intelamd on 2012-10-08
> **Bucky Ball said:**
> If you're talking about the menu at the beginning then hit Shift after the BIOS screen at boot to get a menu.

As for the other issue, are you using any third party graphics drivers or using the open-source default? Looks like it's having problems with your monitor which accounts for the delay.


hi Bucky Ball,


I checked my system for proprietory drivers and it says ''no proprietory drivers are in use" so I think the system is using open source drivers. I also hit shift after the BIOS screen and I just saw a glimpse of "Grub loading" but then it disappeared and it logged into Linux Mint.

---

### Post by Bucky Ball on 2012-10-08
Have you done an update since install? If not do that and check Additional Drivers again. Which release are you using? It used to be 'Esc' key for the menu but then it changed to 'Shift'. Strange that not doing anything. That should be giving you the option to boot to Win or Ubuntu or Mint or whatever.

---

### Post by intelamd on 2012-10-08
> **Bucky Ball said:**
> Have you done an update since install? If not do that and check Additional Drivers again. Which release are you using? It used to be 'Esc' key for the menu but then it changed to 'Shift'. Strange that not doing anything. That should be giving you the option to boot to Win or Ubuntu or Mint or whatever.



I am using Linux Mint Maya 13 Cinnamon. I have completely updated the system.  I am very upset because of this no grub boot selector. I can't log in to Windows because of that and I have important data there. :(

---

### Post by Bucky Ball on 2012-10-08
Well, you should be able to access that data without to much of an issue if that's any consolation. The button to press for the menu is shift in the newer versions of Ubuntu so not sure why it's not the same with Mint. You have the BIOS set to boot from the hard drive that grub is installed on? It should have been installed on sda.

---

### Post by cipherboy_loc on 2012-10-08
Check here maybe for information on changing the grub config. It should tell you how to set the menu to display every boot:

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

---

### Post by Bucky Ball on 2012-10-08
> **cipherboy_loc said:**
> ... how to set the menu to display every boot... 

That's pretty straight forward.

Open a terminal.
Paste this in:

```
sudo nano /etc/default/grub
```Make these lines look like this:
```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```Hit Control+x then 'y' to save and exit. Reboot. You should get the menu for ten seconds (indefinitely if you then hit any key).

It might be a good idea to make a backup before you begin in case you make any mistakes:

```
sudo cp /etc/default/grub /etc/default/grub.bak
```Grub Customizer is the non-terminal way of doing this but not sure if there is an ISO or if you can install it to a Live boot (you can with Boot Repair but that won't help here ... yet).

---

### Post by intelamd on 2012-10-08
hi Bucky Ball,


Now I have some good news and bad news. The good news is that somehow I have been successful to bring grub bootloader to choose which OS to use. The bad news is that when I select Windows XP it does not boot and the grub boot loader returns. This is how I achieved this:


I switched from graphical display to console display. I did the following:


“Open a terminal and run:

Code: Select all
gksudo gedit /etc/default/grub


Find the following line of text, and remove the # in front of it:

Code: Select all
#GRUB_TERMINAL=console


Save and close the file and then run:

Code: Select all
sudo update-grub2


This should make GRUB be able to display again."



Now the grub is there but I can't boot into Windows XP. Is there some solution to this problem? I am very confused. I have hope that you would be able to guide me in this. My best regards.

---

### Post by cipherboy_loc on 2012-10-08
It sounds like somehow your windows boot was messed up during installation maybe? Now would be the time to run the boot info script such that we can see the config there. Since you can get into your Linux side, you should be able to run it there. 

(boot info script in my signature)


Thanks,
Cipherboy

---

### Post by Bucky Ball on 2012-10-08
Now would be the time to run Boot Repair. Think it's in the repositories so just install and launch it. That should add Win to your list. Grub maybe looking but not finding the Win bootloader (Boot Repair should find it) or the bootloader has been screwed as mentioned. If BRepair fails, Boot Info Script it is ... Good luck ...

---

### Post by intelamd on 2012-10-09
> **cipherboy_loc said:**
> It sounds like somehow your windows boot was messed up during installation maybe? Now would be the time to run the boot info script such that we can see the config there. Since you can get into your Linux side, you should be able to run it there. 

(boot info script in my signature)


Thanks,
Cipherboy



Hi Cipherboy,


First I think we should use Boot repair. If that solves the problem then that would be nice. If not then I would use boot info script to see whats wrong actually. :)

---

### Post by intelamd on 2012-10-09
> **Bucky Ball said:**
> Now would be the time to run Boot Repair. Think it's in the repositories so just install and launch it. That should add Win to your list. Grub maybe looking but not finding the Win bootloader (Boot Repair should find it) or the bootloader has been screwed as mentioned. If BRepair fails, Boot Info Script it is ... Good luck ...



Hi Bucky Ball,


Boot Repair is not in the Mint repositories. Is there any other way to find and install it? Kindly inform. Best regards. :)

---

### Post by oldfred on 2012-10-09
Boot repair is not in Ubuntu repositories yet either.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

You can directly install it or download a full repair liveCD.

---

### Post by intelamd on 2012-10-09
> **intelamd said:**
> Hi Cipherboy,


First I think we should use Boot repair. If that solves the problem then that would be nice. If not then I would use boot info script to see whats wrong actually. :)


Hi Cipherboy,


Installed bootinfoscript as Boot Repair could not fix the problem. Now kindly inform how to use this utility? :)

---

### Post by YannBuntu on 2012-10-09
What is the URL returned by Boot-Repair?

---

### Post by oldfred on 2012-10-09
Bootinfo script does not fix any issues. It just gives us info on your exact configuration so we can tell what may be the issues with your system.

But Bootinfoscript is run as part of BootRepair when you run the BootInfo report. Just post link to the report.

---

### Post by intelamd on 2012-10-09
I see. I didn't know about Boot Repair report url. I would again run it and post the link to the report.:)

---

### Post by intelamd on 2012-10-10
Hi everyone,


Below is the complete information I got after using Boot repair. Kindly view and help. :)


                                  ```
RECOMMENDED REPAIR:
 

 

 Boot successfully repaired.  
 

 Please write on a paper the following URL:  
 [http://paste.debian.net/198533/](http://paste.debian.net/198533/)  
 

 In case you still experience boot problem, indicate this URL to:  
 [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.  
 

 You can now reboot your computer.  
 

 

 The boot files of [The OS now in use - Linux Mint 13 Maya] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
 

 

  --------------------------------------------------------------------------------------------------------------------

                                  CREATE A BOOTINFO SUMMARY
 

 

 

 Please write on a paper the following URL:  
 [http://paste.debian.net/198534/](http://paste.debian.net/198534/)  
 

 In case you still experience boot problem, indicate this URL to:  
 [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.  
 

 No change has been performed on your computer. See you soon!
  

__________________________________________________________________________


                                  ADVANCED OPTIONS:
 

 (Backup partition tables, bootsectors and logs)
 

 

 Reinstall Grub:
 

 Boot successfully repaired.
  
                                  Please write on a paper the following URL:
 [http://paste.debian.net/198621/](http://paste.debian.net/198621/)
 

 In case you still experience boot problem, indicate this URL to:
 [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.
 

 You can now reboot your computer.
 

 

 The boot files of [The OS now in use - Linux Mint 13 Maya] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
  

-----------------------------------------------------------------------------------------------------------------------------

                                  GRUB LOCATION
 

 

 OS to boot by default: (Windows via sda7 menu)
 

 Place GRUB into: Sda
 

 

 Boot successfully repaired. 
  
 Please write on a paper the following URL: 
 [http://paste.debian.net/198624/](http://paste.debian.net/198624/) 
  
 In case you still experience boot problem, indicate this URL to: 
 [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum. 
  
 You can now reboot your computer. 
  
                                  The boot files of [The OS now in use - Linux Mint 13 Maya] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
 

  
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

  

                                  GRUB OPTIONS:  Nothing changed as I don't know about the options.
  
                                  

 

 Edit Grub Configuration File:
 

 

 # If you change this file, run 'update-grub' afterwards to update
 # /boot/grub/grub.cfg.
 # For full documentation of the options in this file, see:
 #   info -f grub -n 'Simple configuration'
 

 GRUB_DEFAULT="Microsoft Windows XP Professional (on /dev/sda1)"
 #GRUB_HIDDEN_TIMEOUT=0
 GRUB_HIDDEN_TIMEOUT_QUIET=true
 GRUB_TIMEOUT=10
 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 GRUB_CMDLINE_LINUX=""
 

 # Uncomment to enable BadRAM filtering, modify to suit your needs
 # This works with Linux (no patch required) and with any kernel that obtains
 # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
 #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
 

 # Uncomment to disable graphical terminal (grub-pc only)
 GRUB_TERMINAL=console
 

 # The resolution used on graphical terminal
 # note that you can use only modes which your graphic card supports via VBE
 # you can see them in real GRUB with the command `vbeinfo'
 #GRUB_GFXMODE=640x480
 

 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
 #GRUB_DISABLE_LINUX_UUID=true
 

 # Uncomment to disable generation of recovery mode menu entries
 #GRUB_DISABLE_RECOVERY="true"
 

 # Uncomment to get a beep at grub start
 #GRUB_INIT_TUNE="480 440 1"
 

  -----------------------------------------------------------------------------------------------------------------------------


                                  OTHER OPTIONS:
 

 

 Repair Windows boot files
  
Create a bootInfo summary  
 

 

 Participate to statistics of use
 

 Boot successfully repaired. 
  
 Please write on a paper the following URL: 
 [http://paste.debian.net/198628/](http://paste.debian.net/198628/) 
  
 In case you still experience boot problem, indicate this URL to: 
 [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum. 
  
 You can now reboot your computer. 
  
  
 The boot files of [The OS now in use - Linux Mint 13 Maya] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
```

---

### Post by oldfred on 2012-10-10
You just needed to post the link. :)

You installed grub2's boot loader to the PBR - partition boot sector of the Windows XP NTFS partition. Windows has its boot code in the PBR and has to have that not grub. NTFS does have a backup, so if only installed once you can use the backup to recover the correct NTFS info:

```
sda1: _________________________________________
    File system:       ntfs
[COLOR=Red]    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 300815624 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
[/COLOR]    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM
```Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by intelamd on 2012-10-13
> **oldfred said:**
> You just needed to post the link. :)

You installed grub2's boot loader to the PBR - partition boot sector of the Windows XP NTFS partition. Windows has its boot code in the PBR and has to have that not grub. NTFS does have a backup, so if only installed once you can use the backup to recover the correct NTFS info:

```
sda1: _________________________________________
    File system:       ntfs
[COLOR=Red]    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 300815624 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
[/COLOR]    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM
```Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)




Thanks oldfred. Because of your help I am able to log into Windows XP. I used the method on the following site:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I am very thankful to you. I need to know just one more tip from you. I wish to make Windows XP the default in the Grub boot menu like:

Windows XP (Default and first in the line)
Linux Mint 13

I mean making XP default in a way that the first choice in the boot selector is XP and the second is Mint. How is this possible? :)

---

### Post by kiyop on 2012-10-13
I want to know the contents of /boot/grub/grub.cfg and /etc/default/grub. and the list of files in /etc/grub.d/ , but if there are only one menuentry for windows generated by /etc/grub.d/30_os-prober, you can rename /etc/grub.d/30_os-prober to /etc/grub.d/07_os-prober and execute "sudo update-grub".

Refer
[https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2)

ADDED at Sun Oct 14 12:43:57 JST 2012;

Thanks oldfred for your nice support;
[http://ubuntuforums.org/showpost.php?p=12294055&postcount=28](http://ubuntuforums.org/showpost.php?p=12294055&postcount=28)

---

### Post by Lyfang on 2012-10-13
Is done at your own risk (as usual): You could try to restore the old Windows boot loader: NTLDR and then install GRUB. See also: [http://ubuntuforums.org/showpost.php?p=12059743&postcount=3](http://ubuntuforums.org/showpost.php?p=12059743&postcount=3) and [http://ubuntuforums.org/showpost.php?p=12087651&postcount=4](http://ubuntuforums.org/showpost.php?p=12087651&postcount=4)

---

### Post by oldfred on 2012-10-13
kiyop way works. He actually has referred  to two different ways, one editing grub.cfg and the other changing the order of the scripts. 

Some also like grub customizer.

HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by intelamd on 2012-10-13
> **oldfred said:**
> kiyop way works. He actually has referred  to two different ways, one editing grub.cfg and the other changing the order of the scripts. 

Some also like grub customizer.

HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)



oldfred, actually what I wish to do is to bring Windows XP at the top of the OS selections at the grub menu. I have already made Windows XP the default OS to boot with the help of a utility called "Boot Repair" as you know that I had downloaded it. But though Windows XP is the default it is on the third or fourth of OS selections for eg. 1- Linux Mint, 2- Linux Mint (Recovery), 3- Memtest, 4- Memtest etc. 5- Windows XP. I wish to bring it to the top at number 1. How to do this?:confused:

---

### Post by oldfred on 2012-10-13
kiyop's second method of renumbering the scripts will work.

But if there is a major update to grub2, it may rewrite the default scripts and you then get both the newer and old entries. Should not be a major issue as long as you know.

If you do not want to renumber scripts you can do the same thing with 40_custom. Scripts and custom are added to the menu in the order XX_.  So if you modify 40_custom and copy to 06_custom it becomes the first entry. But then you may want to turn off os_prober to not have duplicate entries.

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
You can just copy Windows entry into a copy of 40_custom, just be sure to include the couple of lines at the top of 40_custom in your copy.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Create  & then copy windows entry to 06_custom:
sudo cp -a /etc/grub.d/40_custom /etc/grub.d/06_custom
gksudo gedit /etc/grub.d/06_custom
Then do:
sudo update-grub

More detail here:
If you save the file you create with the custom entry to, say, 06_custom, it will not be over written and will be at the beginning of your menu
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries]("http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries")

and from Herman's site if your name it 06_custom to be near the top of grub.cfg:
When you are finished putting all of your custom boot entries in your /etc/grub.d/06_custom file, it needs to be chmodded to make it executable,
sudo chmod 755 /etc/grub.d/06_custom
Use a command something like this to change the file permissions to make your file executable.

To turn off os-prober:
gksudo gedit /etc/default/grub:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by Bucky Ball on 2012-10-14
Grub Customizer, as mentioned previously by oldfred, will move the Win selection to the top of the list in a jiffy ...

---

