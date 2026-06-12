---
title: "Grub Commands?"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Smaug067 on 2006-10-25
Hello, all! I test-drove Dapper for about a month before I decided to make it my main OS. My only other experience with Linux was a failed attempt to install Red Hat about ten years ago. I set up my computer with 3 hard-drives: 1st for Ubuntu, 2nd for Win98, and 3rd for DOS. Installation went without a hitch, but now I'm stuck... Upon booting up, my computer displays "grub>". I managed to use the good ole "help" command to give me a list of commands to run from this point, but am at a loss as to syntax, command structures (where in tarnation is the kernel anyway!?!) and am really looking for just a good basic point to start from. Thanks... and I must add.....  Ubuntu ***ROCKS!!!!!***

---

### Post by ReaderRat on 2006-10-25
These may help:
GRUB - HowTo set/change the default OS in GRUB
          **[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)**
GRUB - How To Do Most Anything With GRUB
          **[http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu](http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu)**
GRUB - Community HOWTO >
       [[color=BLUE]**GRUB HowTo**[/color]](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Smaug067 on 2006-10-25
Thanks, RR for your quick response. I have found the [GRUB online manual]("http://www.gnu.org/software/grub/manual/grub.html") and am pretty sure I will be able to get things up and running before too long.

---

### Post by daou on 2006-10-25
Something probably went wrong during the installation if grub boots to manual input.

You should be getting a list of OS's to boot. Or did I misunderstand the situation?

---

### Post by Bigbluecat on 2006-10-25
The best way I have found to fix grub problems is to follow Hermans guide to manually boot the Kernel - see the link posted earlier. 

The step by step commands here take you through the grub commands to find out how grub names your hard drives and where your kernel and boot files are located (in grub naming terms).

Once you know this and boot Ubuntu it is easy to edit your menu.lst file to match what is needed.

Good luck.

---

### Post by Smaug067 on 2006-10-25
> You should be getting a list of OS's to boot. Or did I misunderstand the situation?

daou: No, I think you are correct. I used the Live CD to poke around in my file system and the menu.lst file for GRUB is completely empty. I'm pretty sure I can get things humming along this evening (at least by the weekend;) ).

Thank you all so much for your help!:D

---

### Post by daou on 2006-10-26
I applaud your enthusiasm for learning Grub commands. I had my fair share of problems with Grub when I first started using Ubuntu (RAID array problems, dual boot). Took me a few days to get things working. About two weeks to get it setup just like I wanted :rolleyes:.

But before you burn yourself out ;) trying to figure out what's wrong with Grub, go have a look at this thread:

[How to restore Grub from a live Ubuntu cd.]("http://ubuntuforums.org/showthread.php?t=224351")

It shows you how to reinstall Grub from the LiveCD. I skimmed through it and somewhere someone had a similar problem with the menu.lst disappearing. Don't worry, you'll have plenty of chances to learn stuff along the way. Ubuntu is no cakewalk despite the slogan. At least if you want to modify it to your liking.

---

### Post by Herman on 2006-10-26
A common mistake that beginners make is to think that 'menu.lst' is the same as 'menu.1st'
The command 'sudo gedit /boot/grub/menu.1st' gives me an empty page too.
The correct command is 'sudo gedit /boot/grub/menu.lst' ```
sudo gedit /boot/grub/menu.lst
``` It's short for 'menu list', not 'menu first'.
I'm not certain if that is really what people are doing wrong or not, just a guess.  There could be some other syntax error involved.
Re-installing Grub won't hurt anything though. 

A tip is to get into the habit of using 'tab completion' when you type commands in terminal, just type the first two or three letters of each directory name and filename and press your 'tab' key to auto-complete your filename for you.
For example, type 'sudo gedit /bo'    ..and press tab, then type 'gr' and press tab again, then type 'me', and press tab again. (Just try  it).  :D
Read Kryal's [Terminal for Beginners - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=73885") that will help most people to get the most out of Ubuntu.

On the other hand I have heard of people installing and not having any Grub at all, so it is possible to really have an empty menu.lst I suppose. Things like that would be extremely rare though.
If it was opened in GUI mode it should show some text, most people new to Linux would be more likely to try opening it in GUI mode before trying to do anything with the terminal.
If it was done from a terminal in the LiveCD without mounting the hard disk's partition (filesytem first, that might be the problem too. Here is how to mount your installed Ubuntu with your Ubuntu LiveCD and open your menu.lst file, [Mount Other Filesytems]("http://users.bigpond.net.au/hermanzone/p10.htm")  , and see this part in particular,              [Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

Regards, Herman  :D

---

### Post by catlett on 2006-10-26
you have a command line grub. You shouldn't have to deal with it but it is a working grub believe it or not. Yo can enter the commands from a menu list manually. For instance, this is my grub entry for ubuntu
```
title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,0)
kernel          /vmlinuz-2.6.15-27-686 root=/dev/hda5 ro quiet splash
initrd          /initrd.img-2.6.15-27-686
savedefault
boot
```
You can enter all this at grub> You do not need the titile line, that is for the user when they look at the menu. Anyways, I can boot my system like this from a grub command line.
```
grub>  root (hd0,0)
```
```
grub> kernel /vmlinuz-2.6.15-27-686 root=/dev/hda5 ro quiet splash
```
```
grub> initrd /initrd.img-2.6.15-27-686
```
```
grub> boot
```
Since you already know how to use the live cd to look at your system, go into boot and write down the kernel version (the kernel is the file labeled vmlinuz just in case you didn't know. Also right down the version number of the initrd.
Next enter this in a terminal ```
sudo fdisk -l
```That will list all your partitions. You need to figure out which one holds ubuntu's root. If you just have 1 partition, root is on that one. Usually the installation will put a boot flag * on ubuntu's root.
Once you get into your system, you can install grub again with thsi command```
 sudo grub-install /dev/hda
```using /dev/hda will put grub on your mbr.
Hopefully you are already up and running but if not, hopefully this helps.

---

### Post by Smaug067 on 2006-10-26
Thank you all for you help and advice. When I gave GRUB the "kernel" command, it gave me the dreaded "Error 18". I don't know how to make a boot partition that will marry up with my old BIOS (Gparted's minimum is 2G, I need something more like 50M). I'm going to go with a smaller HD, get things going, and expand/upgrade from there.:p

---

