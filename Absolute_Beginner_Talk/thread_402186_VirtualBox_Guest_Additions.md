---
title: "VirtualBox Guest Additions"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by alteredcarbon on 2007-04-05
Hey all - brand new to Linux.  I installed VirtualBox on a Win2k system with the intention of then installing Ubuntu Edgy on the virtual machine.  So far, so good except now I'm having trouble with Linux Guest Additions.  

To break it down:

Host OS = Win2k 
Guest OS = Ubuntu Edgy
VM = VirtualBox

I did read and reread Ch. 4 in VB's user manual, but I'm stuck after selecting the .iso in VB settings.  It mounts just fine, and in fact, in Ubuntu on the desktop I can see the file "VBGuestAdditions" just sitting there.  And when I open up computer in Ubuntu desktop, I can see that same file has attached itself to the CDROM drive.  It reads "CD/DVD Guest Additions."  

My problem is that I have no idea how to run this thing.  It sits on the desktop and that's about it.  Meanwhile, Ubuntu won't recognize the USB, the floppy drive, my sound card and the video display is pretty crappy as well.  You wouldn't want to sit and stare at Ubuntu in the virtual machine for hours and hours b/c you'd go blind in the process.  Suffice it to say, this does not make for a pleasurable Ubuntu experience.  I suspect all these problems would be resolved if Linux Guest Additions were doing something besides sitting on the Ubuntu desktop.

Will someone pls point me in the right direction and tell me what I'm doing wrong?  I have followed and refollowed, read and reread the VB user manual as it regards using Linux Guest Additions on a Windoze host, but it doesn't do any good. I need someone to break it down from English into moron-ese for me.

TIA.

---

### Post by alteredcarbon on 2007-04-05
was anyone going to help me out here or am I basically SOL on my own?

fyi I have attempted to run the sh ./vboxadditions.run help and all the other little commands suggested by the virtualbox user manual ch. 4 linux guest box addtions in an attempt to get it to run, but the terminal bitches about not being able to open the file for run or help, so apparently I'm missing something and there isn't anyone willing to help me out.  so much for the helpful community theory.  

I guess my options are to spin my wheels round and round asking for help here before ultimately getting banned/shunned because I'm not being sunshiney happy or else just give up on the OS all together.  it's too bad, really, b/c I had an entirely different impression of this community.  I was under the impression people wanted to help stupid n00bs.  Guess not.

---

### Post by jerryrw on 2007-04-05
I've never used VB but if you need to run a script in the Ubuntu Guest you would prolly have to use sudo to run it as root.

sudo sh ./yourscriptname

---

### Post by dmflad on 2007-04-08
I've got opposite set up from yours - I'm running Ubuntu Edgy and have installed VirtualBox so I can eventually run WinXP in a guest container (so I can play Call of Duty2). 

Right now I have a guest set up to run FedoraCore6. After I installed FC6 and had it running I clicked in the VBox tool bar on "Devices" then "Install Guest Additions".  Wish I knew for certain if you do same thing if running VBox on a Win2K PC but thought to pass info along so you can check what you see.

If I get a chance this week I'll see if I can put VBox on my work PC (WinXP) and then install some flavour of Ubuntu as a guest and let you know what happens.

---

### Post by wjston on 2007-04-08
> **alteredcarbon said:**
> Hey all - brand new to Linux.  I installed VirtualBox on a Win2k system with the intention of then installing Ubuntu Edgy on the virtual machine.  So far, so good except now I'm having trouble with Linux Guest Additions.  

To break it down:

Host OS = Win2k 
Guest OS = Ubuntu Edgy
VM = VirtualBox

I did read and reread Ch. 4 in VB's user manual, but I'm stuck after selecting the .iso in VB settings.  It mounts just fine, and in fact, in Ubuntu on the desktop I can see the file "VBGuestAdditions" just sitting there.  And when I open up computer in Ubuntu desktop, I can see that same file has attached itself to the CDROM drive.  It reads "CD/DVD Guest Additions." 

I am unsure what you mean here. Have you actually installed Ubuntu in VirtualBox, or are you stuck at the pre-install stage? I have it running on Ubuntu 6.10, and I have installed four guest operating systems so far (XP, Fedora Core 6, MEPIS, and Ubuntu Feisty 7.04). 

> My problem is that I have no idea how to run this thing.  It sits on the desktop and that's about it.  Meanwhile, Ubuntu won't recognize the USB, the floppy drive, my sound card and the video display is pretty crappy as well.  You wouldn't want to sit and stare at Ubuntu in the virtual machine for hours and hours b/c you'd go blind in the process.  Suffice it to say, this does not make for a pleasurable Ubuntu experience.  I suspect all these problems would be resolved if Linux Guest Additions were doing something besides sitting on the Ubuntu desktop.

When you start VB, is it loading with a menu box - NEW>SETTINGS>START>DELETE buttons? I am going to presume yes, and also that you have created a new drive that you have either installed Ubuntu on or are trying to install it on. When you create the new drive, there is a "Details" pane on the right side that allows you to configure all the above options. You have to click once on the blue title (i.e. [COLOR="RoyalBlue"]Floppy[/COLOR][COLOR="Black"]), and this will open a configuration menu where you can select "Mount Floppy Drive." Go through the list on the left side one at a time until you have either "Mounted or Enabled" all the devices you need. Make sure to make a note of the MAC address in the Network adapter if you have MAC filtering set on your router - otherwise Ubuntu's network manager will not be able to configure a working IP[/COLOR]

> Will someone pls point me in the right direction and tell me what I'm doing wrong?  I have followed and refollowed, read and reread the VB user manual as it regards using Linux Guest Additions on a Windoze host, but it doesn't do any good. I need someone to break it down from English into moron-ese for me.

TIA.

I had never used Virtual Ware prior to last week, and I struggled getting the first OS to install. However, once I got passed the first one, it has become relatively easy to configure more. Just a note - not all OS will install. For example, I tried Xandros and was able to successfully install but, upon reboot, I could not get the mouse to work once I clicked inside the virtual window; consequently, I removed the drive by deleting it and then removed it from "File>Virtual Disk Manger" to purge it from VirtualBox.

Hope this helps

---

### Post by bmt on 2007-04-08
> **alteredcarbon said:**
> fyi I have attempted to run the sh ./vboxadditions.run help and all the other little commands ...
As others have pointed out, you need to run as root, so it's 'sudo <command>'.

Also, Linux is case sensitive -- 'sh ./vboxadditions.run' isn't the same as 'sh ./VBoxAdditions.run'.

From a terminal in the guest os, change directory to the cd-rom image (probably /media/cdrom but check it) and run:
```
sudo sh ./VBoxLinuxAdditions.run
```
You'll need to type your user password (at the 'Password:' prompt).  Note that the password entry will not show anything on the screen -- just type the password and press 'Enter'.

---

### Post by slapdash41 on 2007-04-17
> **bmt said:**
> As others have pointed out, you need to run as root, so it's 'sudo <command>'.

Also, Linux is case sensitive -- 'sh ./vboxadditions.run' isn't the same as 'sh ./VBoxAdditions.run'.

From a terminal in the guest os, change directory to the cd-rom image (probably /media/cdrom but check it) and run:
```
sudo sh ./VBoxLinuxAdditions.run
```
You'll need to type your user password (at the 'Password:' prompt).  Note that the password entry will not show anything on the screen -- just type the password and press 'Enter'.


hi bmt, 

I did what u just said but there is a problem. when first time i boot ubuntu, It seems my VBox hang.I cant even move a mouse or use keyboard on guest machine (Ubuntu) on the first time Ubuntu Login Screen..I need to reset so many time my Vbox..what is the problem actually?..I also install same way on Kubuntu but it seem no problem..:confused:

---

### Post by bmt on 2007-04-23
> **slapdash41 said:**
> I did what u just said but there is a problem. when first time i boot ubuntu, It seems my VBox hang.I cant even move a mouse or use keyboard on guest machine ...
Do you mean:
1. the first time you boot after installing Ubuntu, or
2. the first time you boot after installing Guest Additions?

If number 1, then check all the conditions for the virtual machine -- HDD space, memory allocation, everything else! ;-)

If number 2, remember that guest additions are not *needed* to run the virtual machine -- just enhancements.  In fact, I find the guest additions more useful for a Windows guest than for a Linux guest.  Automatic resizing of the Windows screen is very good, but it doesn't work the same in Linux.

Apart from these suggestions, I cannot offer any more help.  If a virtual machine does not boot, there are too many possibilities for the problem.  I am not an expert!

---

### Post by king4144 on 2008-03-25
This worked for me. I have seamless mouse integration (no wobbly windows with Compiz,
however).

---

