---
title: "Dualboot"
date: 2005-05-29
forum: Absolute Beginner Talk
---

### Post by Hansje on 2005-05-29
I don't find out how to fix it. Which program need I so when i turn on the computer i get a list where i can chose wich operating system i want to use, and if i do nothing it have to boot windows (after 5 sec or something like that). Can somebody help me plz?

Greetz
Hansje

---

### Post by Leif on 2005-05-29
If you install Ubuntu on a computer that already has windows, without deleting windows, it already should be on your grub.

---

### Post by BrianT on 2005-05-29
There are people who know far more about this than me, but I will tell you what I know.

I am using GRUB which installed itself when I installed Ubuntu.  GRUB is the GRand Unified Bootloader.  I am not sure how to do a manual install of GRUB.  The Synaptic Package Manager should install the packages just fine (Search for 'GRUB') and may even have it install it to the boot sector automatically.  

I suspect you may have to install the package and then tell grub to install itself in your boot partition.  Once GRUB is installed and configured, it will give you a list of bootable partitions (Linux, Windows, etc.).

GRUB is located in /boot/grub.  The 'menu.lst' file contains the configuration information.

Let me know how far you get and maybe I can help some more.  Anyone else?

---

### Post by netrattler on 2005-05-29
Please read through once before attempting. Print if necessary.

If you're like most people, you probably purchased your computer from a large retailler. This has pro's and con's but for the purposes of this tutorial we will be concerned with the modifying your current setup.

Firstly, you might want to be a little familiar with the hardware comprising your computer. We will be discussing Hard Drives (hdd, HDD, harddrive).

Your hdd is the device that stores your software - your Operating System and everything associated. Please see the following page for images:
[http://images.google.com/images?q=h...ial&sa=N&tab=wi](http://images.google.com/images?q=h...ial&sa=N&tab=wi)

For the purposes of installing anything on your harddrive, file systems and partitions need to be created. As well, for the purposes of this tutorial only basic information necessary to complete the task is provided.

A partition is simply an organizational structure. Picture your home - the hdd. Now, in your home there are rooms, your partitions. It's that easy.

On your existing hdd is one large partition ( get into it: [http://www.google.com/search?hl=en&...ons&btnG=Search](http://www.google.com/search?hl=en&...ons&btnG=Search) )that the manufacturer of your computer has created to install the operating system and ancillary programs.

Your computer can be better utilized by re-partitioning your (no doubt giant - 60-200 GB) hdd. This can be accomplished in such a way that you keep your current installation of Windows intact and useable following this tutorial.

For the purposes of this tutorial it is necessary for you to goto: [http://www.sysresccd.org/download.en.php](http://www.sysresccd.org/download.en.php) and download, then burn, this disc. You will be booting to this disc to accomplish this task.

----------

If necessary - back up whatever it is that you would NOT LIKE TO LOSE. YMMV, I have never lost data this way but a prudent person has a backup. As well, I have used and recommend the program: NTFSResizer. It is a small program you put on a floppy and boot to in order to resize your NTFS partition(s). You might consider using this method to resize your current Windows XP (NTFS) partition instead of booting to the systemrescue disc. I like the systemrescue disc because there are other very useful utilities on it. Either way you're good.

This tutorial assumes you have a comfort level running programs. I assume you will be able to navigate graphical programs to complete this task.

----------------end long-winded intro--------------


Insert the SystemRescue Disc into your cd-rom (your master, if applicable). Reboot your machine to the cd-rom drive (if necessary you will need to change a BIOS setting to allow this. Google it.)

You will be greeted with a prompt shortly, at this point type: menu, hit enter.
At the next prompt: arrow right, then down to select Rescue. Hit enter.

Let it boot.

At the next prompt, when it's finished booting, type: run_qtparted, hit enter.
At the next prompt, choose your mouse. For a ps/2, just type: 3, hit enter.

When QTParted opens you will see that it's a familiar looking application. It's sectioned. On the left, in the column at the top you will see your hdd's. It probably reads: hda.

If you would please, click on that hda. Now, to your right in the other column you will see your partitions. You probably see only 1, and it occupies all of the space on your hdd. We can resize, or delete this partition. NOTE: this partition has your Windows installation on it, so if you are keeping that, we are RESIZING now.

If you would, please click on your partition; either the large "bar" image over the right column, or your partition in the right column. I think you can right click and choose "resize". If no, then click the partition and look up in the menu for the option to resize. Choose resize.

You will be greeted with a window with another "bar" image representing your large partition. You will see that it has "handlers" on either end. Grab the right-side one with your mouse and drag it left. Keep it to 2GB**. You just resized it. Hit OK or whatever it says (I am writing this from memory).

Now, in your menu - find the option to "commit" and choose it. Don't let the warning messages scare you - it's your hdd and you're in charge.

Now, you will see that the rectangle image representing your hdd has changed. You will see inside the rectangle now a small partition on the left side. Now you may click on the whole rectangle and right-click and choose "create". In this way you may create more partitions. Keep this in mind: You may only have 4 "Primary" partitions on your hdd. However, you may make many "Logical" partitions. In this tutorial we make 3 other partitions. They are all Primary.

To keep things simple we'll use the following architecture (40GB hdd):

hda1: winXP, C:\, NTFS, 2GB** (set ACTIVE, if not already)
hda2: linux, /, ext3, 10GB
hda3: linux, /home, ext3, 27.75GB
hda4: linux, swap, 250mb

Arbitrary partition sizes. For swap (if even necessary. Have 1GB RAM? Then no swap - you'll never need/use it.) I usually create a partition equaling about 1/2 my RAM.

** Sizing up your partitions is really subjective. I have no idea how many programs you have installed or the real size of your current partition use. You may need 5 or even 10GB for your current windows installation. I don't know, you do. Change sizes to reflect your needs.

-------------
This tutorial does NOT address backing up your newly resized, existing windows partition. I will write another one for that purpose. Prudent folk have backups.
-------------

Close the QTParted program. You are now back at that prompt. You may now type: reboot, hit enter. You will reboot, during reboot - quickly, replace the SystemRescue Disc with your Ubuntu Installation Disc.

You will be greeted with An Ubuntu Logo install routine, just hit enter to begin the installation. Soon enough into the installation a Partition Manager will open in order to tell the installation routine where to install Ubuntu and your other directories (/Home, et al.)

You just made your new partitions so during this phase of the install, you wouldn't want to allow the installer to wipe your drive. You'll want to be in command of your partitions, so pay attention to the prompts during install. At the Partition Manager you want to manually effect your drive.

"Manually partition your hdd" (it reads something to that effect) is one of the choices you will be prompted with in the Partition Manager. Choose it. Be careful you don't select to format entire drive, or similar - You will see what I mean, use your arrow keys to select to Manually edit your harddrive.

Next screen appears with your hdd partitions; use your arrow keys and enter to select and modify:

**** You have an opportunity here to resize your partitions; by deleting and re-creating. Some people like to manage their partitions with the install routine of a linux distro. More power to 'em. I like to use other options. So at this point you might decide to change your partition scheme, or resize, or whatever. I'm not saying do it, I'm just letting you know that you could. ****

On your first partition, ( hda1), the Windows one we just saved, choose to not use it, (you may mount it later if you like). Arrow right down to hda2. Choose to use this - you will see, use your enter key to make selections here.

hda2 will be your "/" directory . You should let the install routine reformat your partitions...it only takes a second. Choose to use this partition, choose ext-3 file system, / mount point, and then arrow down to Done.

hda3 is your /home directory. Repeat steps for hda2, labeling it /home.

we made hda4 swap. It's ok to ignore this, it's found already. When you have finished, arrow down to the bottom of the page and choose Done - or the like.

Next screen, Yes to allow the changes - then continue with your install.

Finally, you will be prompted to allow Grub to be installed. Grub has seen your Windows partition/installation already - it is safe. Allow Grub to be installed, where it wants, and you will be good-to-go.

Your machine will reboot shortly. At this reboot it is necessary to go into your bios and choose to Boot to HDD-0. Please see another tutorial for this purpose. It's easy, don't fear this.

Leaving your BIOS, your machine will reboot and in about 2 screens you will see GRUB at the bottom of your screen - hit the ESC key. Do you see that? It is listing your new Ubuntu installation as a choice to boot to, and it is also listing - at the bottom - your Windows installation as a choice as well.

Choose Ubuntu. You did it.
---------------------------
I need a mighty DISCLAIMER right about now. I'm not at all experienced writing tutorials. My writing style, and the horrible edits, will probably leave folks confused, sorry. I hope this helps some folks that would normally be scared to attempt this. Sure, it's an intermediate (?) level task, I suppose, and things CAN and just MIGHT go wrong. Sure, there are any number of ways to accomplish this, as well. The one I mention I employ frequently and with good results, as I said, I have never lost data - but I have had to perform rescues of a more advanced sort. I don't know the condition of your hdd or your panic level.

It's just a hdd, and it's a routine task to partition it. Even resizing is common - and hey, give NTFSResizer a go. It really is good (and free - or was a few years ago when I found it), and you can still make new partitions when you are installing Ubuntu, with the Ubuntu installer's Partition Manager.
--------------------------
Happy Computing

Any mod might think this or the other thread to be redundant now. Feel free to delete at will. As well - this tutorial (Oop, Ack!) screams for an editor!

---

### Post by Jenda on 2005-05-29
Not completely sure, but I think the installer contains NTFSresizer in it.

I resized a friend's NTFS partition perfectly with it. No credit of mine, that's for sure.

---

### Post by Hansje on 2005-05-29
Ok, i just install ubuntu and grub install itself if windows is somewhere there. I give it a try, thanks for the good information

Hansje

---

### Post by Hansje on 2005-05-30
OK, works fine, Grub is installed, but can someboddy tell me how to change the options? Microsoft windows must be the default boot. How can i do this? This is my menu.lst:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
``` 

Thanks
Hansje

---

### Post by tread on 2005-05-30
I think its the default at the beginning of the file .. but you might want someone to confirm this cos I don't remember.

---

### Post by bored2k on 2005-05-30
Tip: use Grubconf, it is a graphical representation of this .
```
wget http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb && sudo dpkg -i grubconf_0.5.1-4ubuntu2_i386.deb
```

---

### Post by Hansje on 2005-06-01
[QUOTE=bored2k]Tip: use Grubconf, it is a graphical representation of this .
```
wget http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb && sudo dpkg -i grubconf_0.5.1-4ubuntu2_i386.deb
```[/QUOTE]
 How does it works? i can't open it. I read that it must be executed from the root folder, but i can't copy to there...

Greetz
Hansje

---

### Post by bored2k on 2005-06-01
[QUOTE=Hansje]How does it works? i can't open it. I read that it must be executed from the root folder, but i can't copy to there...

Greetz
Hansje[/QUOTE]
 In a terminal type
sudo grubconf

---

### Post by Hansje on 2005-06-03
Sorry, I don't understand what you mean with terminal type can you explain please?

Greetz
Hansje

---

### Post by GrumpySimon on 2005-06-03
[QUOTE=Hansje]Sorry, I don't understand what you mean with terminal type can you explain please?

Greetz
Hansje[/QUOTE]
 Click "Applications -> System Tools -> Terminal"

Inside the terminal type:
sudo grubconf

--Simon

---

### Post by snds24 on 2005-06-03
Hi, all!
My question is about triple boot.
I have Mepis and WinXP, and GRUB is installed on MBR. I want to add Ubuntu. 

> Install a boot loader

If the installer detects other operating systems on your computer, it will add them to the boot menu. 

The installer will now tell you that the first stage has finished. 

Remove the CD and hit Enter to reboot your machine. It should boot up into the second stage of the installation process.

This is from the Ubuntu install guide and it's not clear to me whether i have a choice during installation to install GRUB on MBR or on root partition.
Thanks.

---

### Post by Lista on 2005-07-22
First, hi to everyone!
I hate opening new topics for my stupid questions, so I'll just use this one. I hope you guys don't mind, and if you do, feel free to do whatever you want with my post. 
Now, when we solved all those techical problems, I have a question to ask. 
I, like everyone else, am trying to get a dual boot with Windows working. At the moment, im only reading up, 'cause I fear losing my data, and I don't have any easy way to back it up!
Now, I understand everything about partitioning and so on, but in Ubuntu installer, it sais that my 200GB HDD has 1,8GB taken, and everything else is free space, when in fact, I have like 150GB of data stored. So, im afraid to make partitions in that 'free' space in fear of losing some of that data!
Any information will be greatly appreciated!

---

### Post by WirelessMike on 2005-07-22
Defrag first.  Let that marinate for as long as it takes.  Then resize the ntfs partition and install Ubuntu on new partitions in the leftover space.  Grub should install itself and it really should be as easy as that.

---

