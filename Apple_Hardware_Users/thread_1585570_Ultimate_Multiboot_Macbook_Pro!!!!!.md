---
title: "Ultimate Multiboot Macbook Pro!!!!!"
date: 2010-09-30
forum: Apple Hardware Users
---

### Post by TGIK on 2010-09-30
I had explained in another post how I got my triple boot (OSX Tiger, Ubuntu 10.4, Windows XP) to work smoothly ---- 

The latest triumph is getting a triple boot on an ext HD---

There are not many success stories involving booting linux off of USB on mactels--- but I have always had luck  booting both Grub2 and Legacy Grub systems off USB (I believe this is because MBP 1.1 was the open and flexible early model)------ though Grub2 systems boot very slowly --- this is why my 'main' Ubuntu 10.4 OS is located on my internal HD -- 

But both Fedora and SUSE boot very quickly ---hmmmm---  I have been able to boot both distro's on an MBR drive and also a GPT/MBR hybrid with the help of gptsync for linux or command line for OSX 10.5 + [becuase ReFit's only handles sync for internal drives]. 

On my Lacie 250GB ext I can boot Fedora 13  or an OSX 10.5.8 clone ---- this disk is a GPT/MBR hybrid --- layout is as follows (sizes innaccurate) 
[SIZE=3]
[B][SIZE=2]---sdb1  EFI system partition       200mb
---sdb2  OSX 10.5.8                     100GB 
[/SIZE][/B][/SIZE]**[SIZE=2][COLOR=black]---sdb3 [/COLOR][/SIZE]**[SIZE=3][B][SIZE=2] Fedora 13                       120GB
---sdb4  Linux Swap for Fedora       6GB [/SIZE][/B]

[SIZE=1]When I start my computer with this drive plugged in the refit menu shows 5 options --- 
[I][SIZE=2]
-mac OSX 10.5.8 [ext] 
-Mac OSX 10.4.11 [int] 
-Linux on Partition 3 [ext] 
-Linux on partition 3 [int]
-Windows XP off partition 4 [int][/SIZE][/I]

Awesome right? Yes but not enough -- a good start --

I realized that there isn't much point in limiting myself to the number of primary partitions allowed in a GPT/MBR setup ---- (though I have been told there are ways around it --- it seems like a hassle) ---- So I keep this disk as my Linux/OSX dual boot EXT--- 

But what about multiple Linux distros on the same drive using one of their bootloaders to load them all?  

I chose OpenSuse to be the main OS on this next 'multi-linux' drive !!!!! 
So I made an MBR partitioned disk drive with 3 partitions that I labeled for myself for later----

[B][SIZE=2]sdb1- Swap
sdb2- Root
sdb3- Mint
[/SIZE][/B]

During the install of SUSE I always choose expert partitioning --- OpenSUSE generally wants to make a seperate partition for it's home folder --- Using expert ; I choose not to do this -- the drive table is as follows -- 

[B][SIZE=2]sdb1- Linux Swap for SUSE [also where Grub boots from] 
sdb2- '/' for OpenSUSE 11.3
sdb3- EXT4 filesystem (to use later to install linux Mint) 
[/SIZE][/B][SIZE=1]

I choose for the bootloader to not boot from MBR. or '/' partition, I choose 'custom boot partition' and choose 'sdb' --this actually with make the system boot from sdb1 (it uses a small piece of swap space) 

After install I restart and the ReFit menu shows me the options : 

[/SIZE][/SIZE][/SIZE][SIZE=3][SIZE=1]
[I][SIZE=2]-Mac OSX 10.4.11 [int] 
-Linux on Partition 1 [ext] 
-Linux on partition 3 [int]
-Windows XP off partition 4 [int][/SIZE][/I][/SIZE][/SIZE]

Suse boots from 'linux on partition 1' --- Awesome got Suse working!!!! --- now to install Linux Mint LXDE on that open EXT4 partition--- Follow the install process (same as Ubuntu's install) and at step 4 choose to pick partitions yourself --- choose the swap that you use for OpenSUSE and click to 'not use partition' [that would destroy your bootloader] --Choose the unused EXT4 and mount as root '/'  (chose not to format since it was alreadt formatted-- and the installer will erase any conflicting files *generally) --- It of course gives you the warning about not making swap space but ignore it (you will make a swap file later) 

Install finishes----- Boot back into OpenSUSE and open bootloader--- this will allow you to add an entry to the menu--- (this step could be it's own story -- if you have questions about this step-- cause there was a learning curve etc.... let me know) -- I correctly wrote in the grub file through YAST where the mint image was and how to load it ---- 

Rebooted --- chose Linux of Part 1 (SUSE)-- in the menu I could choose 'linux other' and this booted my Mint install --- Success!!!! this gave me even more inspiration so I resized my Mint Partition and created an extended partition with an EXT4 and a  swap and installed the ubuntu based 'jolicloud' on it --- Went back to SUSE and added it to my menu ---- 

So now I have a triple boot ext HD drive !!!!---- Again if you want more detail on the menu entry addition part -- ask me -- though YAST makes it somewhat straight forward --- 

I call it the ultimate multiboot becuase if I have my Fedora and SUSE drive plugged in when I boot up I get this list of OS's 
[SIZE=3][SIZE=1][I][SIZE=2]
-mac OSX 10.5.8 [ext] 
-Mac OSX 10.4.11 [int] 
-Linux on Partition 3 [ext] 
-Linux on partition 3 [int]
-Linux on Partition 1 [ext]
      *OpenSUSE 11.3
      *Linux Mint LXDE
      *Jolicloud 1.0 
-Windows XP off partition 4 [int][/SIZE][/I][/SIZE][/SIZE]

---8 options !!!! really fun---- the next step is getting a BSD or Solaris system running --- I actually was able to boot Haiku Alpha off of a drive but it bugged out and messed things up-- Cheers -- let me know if you want step by step parts --- too much to write at this point -- just want to share my success with you guys --- cuz it is forums like this where I learned how to do everything!!!! Thanks Yall
[SIZE=3][SIZE=1][SIZE=1]
[/SIZE][B][SIZE=2]

[/SIZE][/B]

[/SIZE][/SIZE]

---

### Post by linuxopjemac on 2010-10-01
Congratulations.

---

