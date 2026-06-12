---
title: "Ubuntu ate my windows boot"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by smithman89 on 2006-09-15
So, 2 days ago i installed Ubuntu 6.06.  The installation went fine, and after doing some looking around, i wanted to return back to windows.  Now before i continue, let me give some background info for my system.
1.  I installed/had Win XP Pro before installing Ubuntu
2.  Windows is on an old PATA HD, designated /dev/hda1
3.  Ubuntu is currently on a new SATA HD, with designated partitions on /dev/sda1,2,5  (not custom partitioning)
4.  I have tried some things i found in other posts and threads relevant to this, so the basic gist of my grub.lst file looks as so:
> 
title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot
title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd0,0)
makeactive
chainloader	+1
boot
5.  When i used XP Pro, i had Norton GoBack installed, which would boot before regular windows usually.
Ok, so what i basically see when i start the computer up is the basic GRUB menu.  Displaying Ubuntu, ubuntu safe mode, and memtest in the top portion.  On the bottom is my Windows XP Professional selection.  When i select XP Pro, what happens is it starts to boot, then restarts the machine and returns to the boot menu.  So basically Ubuntu is the only one that works.  I know that i didnt kill my windows drive, i mounted it successfully and can access files.  If someone could please help me.

---

### Post by canadianwriterman on 2006-09-15
I don't know if the difference in drive types makes a difference, but I did notice some differences in your menu.list and mine. In mine, for the Windows entry, there is no "boot" at the end and also  it just says "root" and not "rootnoverify."

Again, I have no idea if it makes a difference, but I also have:
```

### END DEBIAN AUTOMAGIC KERNELS LIST
```

before my Windows boot options. So, try editing the menu.list and make those changes. If it doesn't work, you can always edit them back to the way they were.

---

### Post by smithman89 on 2006-09-15
i know it isnt what the default is, it was something i picked up from a different topic i found.  It didnt seem to help, could you post your default grub settings under Windows XP please?  Also, that bit of code you printed, isnt that just a comment?

---

### Post by slimdog360 on 2006-09-15
yep, its a comment and doesnt make a difference. But thats about all I know Im sorry. It looks right to me so I dont know whats going on.

---

### Post by bulldog on 2006-09-15
If windows start to boot,there's nothing wrong with GRUB.
Grub only points the path.

But when booting windows fails without a Grub error,you should look in your XP for the fault.

---

### Post by Najand on 2006-09-15
grub menu.lst is  different when you have a system;
if you write yours, we can help you edit it.

---

### Post by smithman89 on 2006-09-15
Ok, i should be a bit more specific.  When i try to boot windows:  1st. The normal sequence of GRUB executable lines pops up.  2nd  The Windows XP logo appears and loads for maybe about 10 seconds.  3rd.  Then a blue screen pops up with some lines of code that disappear too fast for me to see.  4th.  My computer restarts.

---

### Post by canadianwriterman on 2006-09-15
My menu.list is as follows:

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Recovery 
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by Najand on 2006-09-15
> **smithman89 said:**
> Ok, i should be a bit more specific.  When i try to boot windows:  1st. The normal sequence of GRUB executable lines pops up.  2nd  The Windows XP logo appears and loads for maybe about 10 seconds.  3rd.  Then a blue screen pops up with some lines of code that disappear too fast for me to see.  4th.  My computer restarts.

It seems like a windows problem not grub. Can you mount your windows partition and copy and paste your boot.ini file here?

---

### Post by JayTee on 2006-09-15
> **smithman89 said:**
> Ok, i should be a bit more specific.  When i try to boot windows:  1st. The normal sequence of GRUB executable lines pops up.  2nd  The Windows XP logo appears and loads for maybe about 10 seconds.  3rd.  Then a blue screen pops up with some lines of code that disappear too fast for me to see.  4th.  My computer restarts.

I think what's happened here is that one of your Windows boot files may have become corrupted. Try booting from your Windows XP disk and selecting Recovery mode. This will prompt you with a command window and display the Windows volume usually 1:Windows and asks you to select the Windows install you want. Press 1 and it will ask for your administrator password. If you set one when you installed Windows type it and press enter. If you didn't set it or Windows was installed on the computer by the manufacturer just press Enter. Then at the C:\Windows> prompt type the command "fixboot" and then restart after that completes. Try booting into Windows then.

---

### Post by smithman89 on 2006-09-15
would a windows XP Home edition disc work for fixing the XP pro boot?  Anyone know, cause i kinda dont have my Pro disc, but i have a Home edition disc.  Here is my boot.ini file

> 
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn



---

### Post by Najand on 2006-09-15
Does pressing F8 (keep pushing after selecting windows in grub) when booting Windows help you to see windows boot menu?

---

### Post by smithman89 on 2006-09-15
> **Najand said:**
> Does pressing F8 (keep pushing after selecting windows in grub) when booting Windows help you to see windows boot menu?

lemme try, i havent done much outside of messing with the grub settings, which dont seem to be the problem.

---

### Post by jordanmthomas on 2006-09-15
an XP Home disk can fix the boot problems for Pro.  
Remember, though, that if you use FIXMBR it will clear out grub (which you can restore using the link below if you feel the need to use FIXMBR for some reason)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by smithman89 on 2006-09-15
ok, i can access the windows boot menu from pressing F8 after selecting XP Pro from the GRUB menu.  Is there anything there that can help me?

---

### Post by Najand on 2006-09-15
Can you enter the Safe Mode?

---

### Post by smithman89 on 2006-09-16
So, i tried safe mode, and the results were a bit different.  After selecting safe mode, a list of (what i think are) bootup programs, along with their filepath, partition, and HD designation.  Many popup until they stop at a certain process, that i know is associated with either the Norton Goback program i use, or something to do with my Norton SystemWorks.  Im going to try my XP Home disc, and run fixboot today.

---

### Post by Najand on 2006-09-16
OK... Sounds like you found the problem... Congratulations...

---

### Post by smithman89 on 2006-09-16
Ok, so i guess the next question would be, How do i fix it?  Norton GoBack was one of those recovery programs that would boot before Windows did (to allow the user to fix any problems before Windows booted), but since i installed Ubuntu, GoBack hasnt booted at all.  Im guessing the GRUB and/or Windows boot just bypasses it.  If I try the fixboot from the Windows CD, will i have the same problem with Norton GoBack?

---

### Post by Najand on 2006-09-16
Hmm, it is about norton... Isn't there any documentations about their software? I don't know much about Windows Softwares... Sorry.

---

### Post by bulldog on 2006-09-16
I don't know GoBack at all,can't say what happens.

But if you want any advice,remove the symantec programs,all of them.

Have to say I haven't had good experience with Symantec lately.

You could try latest good boot in windows.

But if it fails either you could use fixboot or even fixmbr from your systen disk.[when safe mode doesn't work]

When you can boot in safe mode you can uninstall the programs which are responsible for the failure.

---

### Post by smithman89 on 2006-09-16
For the "Last Known Good Config", im sure that includes GoBack, ive basically had SystemWorks since i built my computer.  And About the Documentation, there isnt a whole lot of it on the norton support site.  If the fixboot does work, the first thing i will do in windows is uninstall goback, to prevent this from happening again.

---

### Post by bulldog on 2006-09-16
Fixboot or fixmbr will work,you only lose GRUB then,but that's easy to deal with.

Just try it and keep us posted.

Succes,you might need it :)

---

### Post by xpod on 2006-09-16
This exact same thing happened to me recently but before i realised i should have just tried fixing my xp boot with fixmbr i had already wiped the lot and started again.....I did`nt have the luxuary of an xp cd at the time though.

I dont know why it happened ...ALL i did was fit a third hd,check it was all detected fine in both xp and ubu then i put the pc back together and upon reboot it had dissappeared......well,i thought it had..it was actually still there but could`nt be seen..as i only later discovered#-o

---

### Post by Najand on 2006-09-16
Hmm, I think Fixbooot and fixmbr will work too; but as a recommendation, better to remove those nasty Symantec Applications... They give me headache...

---

### Post by smithman89 on 2006-09-17
Ok, sorry for the wait.  I am currently using the boot cd to try to fix the problem.  Fixboot on its own doesnt do the job, i will try fixmbr.

---

### Post by smithman89 on 2006-09-17
ok, now something has really gone wrong.  I used fixmdr, and it first eliminated GRUB, but now there is a bigger problem, XP Pro wont boot still.  It loads past the windows screen with the moving bar.  A new screen loads, and displays text saying that autochdisk is not found, cannot perform check disk.  then the computer sits for about 20 seconds before turning off.  I cant access Ubuntu w/o the live disc, and im trying to see if i can repair my GRUB and/or regular linux boot from the disc.  I could really use some help now.

---

### Post by argie on 2006-09-17
I haven't used Windows in a long while, but I think there was an option for "Step by Step Confirmation before boot" or something like that in the Windows Boot Menu (that one with the Safe Mode and all). 

Why not choose that and just skip the norton process before starting windows? When you're inside windows I think "msconfig" can be used to stop running that norton thing.

Also, about restoring grub:
> **jordanmthomas said:**
> 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by smithman89 on 2006-09-17
Ok, so here is the final verdict on my epic adventures through Ubuntu and Windows.  I ended up having to re-install Ubuntu, because the GRUB fix didnt work (good thing i didnt have alot of stuff on it).  Now the only problem is that i cant mount my windows drive.  I think i should have just kept it the old way...  Oh well.  My plan for the future is to get a hold of my XP Pro disc, and install that over Ubuntu (Sorry guys, but there is no way i will have both linux and windows on my computer, unless i do alot of crap).  I will then (hopefully) be able to transfer my files from the old windows HD to the new one, then wipe the old drive, format it, and use it with windows.  Linux was kinda cool while it lasted, but i guess in the end, it was too much work, just to get it right.  I will use ubuntu until i can install windows again.  Thanks to everyone for helping me.

---

### Post by gn2 on 2006-09-17
Pity you're throwing in the towel so easily, do you really want to be paying for Vista (and other MS compatible software) some years down the line when XP support gets turned off?

Suggest you try again, but don't install grub on the Windows hard drive...
If you want to Dual-Boot, use dual hard drives.... Much safer.

A simple alternative for the noob (like me) is to have a go with PCLinuxOS.
This has an easy to use installer which will install on a USB2 hard drive for you.

That way you can fiddle about learning with Linux and keep your XP drive safe from becoming a Grubby mess.

---

### Post by gn2 on 2006-09-17
Another thing popped into my head just now, why bother with Go-Back when you've got Windows System Restore?

Seems like it's Symantec that's the problem, not Ubuntu...

---

### Post by smithman89 on 2006-09-17
Ok, to the last guy, i know that ubuntu isnt the problem, but it did trigger the problem.  I am using dual HDs for my dual boot, the current problem now is that when i used the fixmbr command, it wiped grub(expeceted), but the thing was, windows still couldnt boot.  At one point i was OSless.  fixmbr also did something, so now i cant mount the drive.  Ubuntu says:"You cannot mount this drive because /dev/hda1 is not removable".  Hopefully, my windows drive isnt corrupted, and i can get the files after i install Win XP Pro over ubuntu.  I really hope that fixmbr didnt compromise the integrety of NTFS on the HD.  So basically right now i am starting out new on Ubuntu.

---

### Post by bulldog on 2006-09-17
Sorry, I understand the need of repairing your computer as soon as possible,but I have to sleep once in a while and do some other things which are important to me.
With the live cd you can restore GRUB and mount your windows for copying stuff.
It can't repair your windows however.
But you can install windows on the same partition where it was before [it will complain] and access your data.
BUT DO NOT FORMAT OR RESIZE.


Fixmbr is only removing GRUB and install the windows boot.

To restore GRUB do the following:

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)


Finally exit the grub shell
Code:

quit 

It is perfectly possible to install grub where ever you want,not on the windows boot disk but on the ubuntu boot disk instead is no problem at all.
Even on a specific partition is possible.

---

### Post by bulldog on 2006-09-17
To mount your windows using your live cd.

sudo mkdir /mnt/windows

makes a mount directory

sudo mount /dev/?? /mnt/windows

mount your windows drive,you have to fill in ?? with your windows partition.

to find out where that is

sudo fdisk -l

gives you a list of all your partitions,just pick the windows.

---

### Post by JayTee on 2006-09-17
I wouldn't scrub Ubuntu if I was in your position. I'd just get my XP Pro disc and boot from that. Then in the text portion of setup I'd choose Install instead of Recovery. When it finds the previous installation of Windows it will give you and option to either install over it or repair it. Choose repair and that may get rid of the boot problem. If it doesn't, you'll need to reinstall over the old one and all your application specific information in the Windows registry will be lost so you'll have to reinstall your apps as well. Unless you've exported all your registry keys to reg files you can import into the new registry which most people do those are the only choices you're left with. For more info on setting up dual boot check out some of the How To's on this site and also check this site out. 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Best of luck getting things back to normal.

---

### Post by imnotrich on 2006-09-30
This happened to me tonight also, using 6.06.1 in a dual xp home/ubuntu setup.

I was upgrading the kernel from the standard 386 version to the 686 (for my celeron d cpu) using the synaptic package manager. 

When I finished, it had overwritten my menu.lst to exclude the windows boot. 

THANKFULLY the genius who wrote the upgrade script thought to have it create a backup menu.lst, from which I simply cut and paste the old grub instructions and POOF all better. 

Ubuntu Rocks!

---

### Post by RasutoIbuki on 2006-10-11
Alright, time to add my two cents.

I too share this same problem, however, I do know the cause. The Blue Screen that pops up is a stop error. The stop error given is the one that points to is a problem with Windows XP and the hard drive controller. Windows XP writes information about the hard drive controller to the OS on the install, which includes information about the MBR. So, when GRUB installs on the MBR Windows decides to freak out.

I haven't had the problem where you can't boot into Windows after using fixmbr. 

My question is can I write information to Window's boot.ini to have that boot into Ubuntu?

---

### Post by gn2 on 2006-10-11
> **RasutoIbuki said:**
> Alright, time to add my two cents.

I too share this same problem, however, I do know the cause. The Blue Screen that pops up is a stop error. The stop error given is the one that points to is a problem with Windows XP and the hard drive controller. Windows XP writes information about the hard drive controller to the OS on the install, which includes information about the MBR. So, when GRUB installs on the MBR Windows decides to freak out.

I haven't had the problem where you can't boot into Windows after using fixmbr. 

My question is can I write information to Window's boot.ini to have that boot into Ubuntu?

I've had similar problems in the past, but I do it this way now:

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)
.

---

### Post by RasutoIbuki on 2006-10-12
I'm pretty sure now my problems were caused by my SATA drives. Thanks for your post but I've decided to do it a different route. I'm now using WINGRUB.

If anyone else stumble upon this thread that has the problem where they blue screen or if it just restarts when they try to select Windows in GRUB I'd be happy to tell them how I got it to work. Just give me a PM or request the info in this thread.

---

