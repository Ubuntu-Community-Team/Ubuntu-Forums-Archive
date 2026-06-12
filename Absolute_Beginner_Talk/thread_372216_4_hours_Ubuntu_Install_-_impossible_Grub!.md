---
title: "4 hours Ubuntu Install - impossible Grub!"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Chrisp7 on 2007-02-27
Hi everyone:) I have heard great things about Ubuntu so thought I'd giv it a try however so far.. Ubuntu is driving me spare, I hope it gets easier!:)

I have partitioned/installed my new hard drive as follows:

Vista - Primary
XP - Primary
OSX - Primary
Extended  - Linux /
                   - Linux Swap
                    -Linux Boot

and have installed Ubuntu successfully however Grub just wont start. I have tried reinstalling, creating a separate boot partition and installed, tried restoring gurb (using the advice here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351))

However nothing at all works!

All I get is: "reboot and select proper boot device or insert boot media in selected boot drive and press a key"

Now I can get into my installed Ubuntu via inserting the install CD and selecting the option to startup with the install on the disk (and at this point it mentions Grub). But Grub just doesnt seem to work on startup - please please can you guys help.

Cheers:) 

ps - with GPart - I have tried (at different occasions) selecting the / partition and the /boot partition as boot.

pps - One other thing - v important - my internet connection cuts off after about 4 mins browsing and I have to restart ubuntu to be able to use it again!

---

### Post by Adramelech on 2007-02-28
I think you can only boot from primary partitions, try making a primary partition for ubuntu.

---

### Post by rccharles on 2007-02-28
> **Chrisp7 said:**
> Hi everyone:) I have heard great things about Ubuntu so thought I'd giv it a try however so far.. Ubuntu is driving me spare, I hope it gets easier!:)

I have partitioned/installed my new hard drive as follows:

Vista - Primary
XP - Primary
OSX - Primary
Extended  - Linux /
                   - Linux Swap
                    -Linux Boot


Looks like you have an Intel mac.  Why don't you see what OS's your mac thinks you have.  Hold down the option key ( or alt key on a pc keyboard ) while you powron the machine.  Pick one to boot.

What is the brand and model of your computer.  I heard that Ubuntu isn't officially supported on an intel mac and I heard that people have gotten Ubuntu to work on an intel mac.  I read were people who have gotten Ubuntu to work on an intel mac have reported some problems getting the machine to book.  Look around.

I am almost sure that I have seen Ubuntu boot from an extended partition.  Don't know about the intel mac.

Have you thought about parallels?  This way you could get all your OS to run at once.
[http://www.parallels.com/en/products/desktop/](http://www.parallels.com/en/products/desktop/)


Robert

---

### Post by Chrisp7 on 2007-02-28
> **Adramelech said:**
> I think you can only boot from primary partitions, try making a primary partition for ubuntu.

Hi:)
I was told differently, that linux can boot off extended, the problem is in addition to those partitions listed I have 200gb of unpartitioned space and If I make linux primary I cant use that can I?

---

### Post by Tomosaur on 2007-02-28
I don't have much experience with Macs - but it looks like it's still trying to boot from a CD. Did you have to change some option to be able to boot the LiveCD? If so, change it back to booting from the hard disk.

---

### Post by Chrisp7 on 2007-02-28
Sorry I was just about to reply, Im on a PC not a mac! I should have said OSX86 I guess.

One other thing - v important - my internet connection cuts off after about 4 mins browsing and I have to restart ubuntu to be able to use it again!

---

### Post by Tomosaur on 2007-02-28
> **Chrisp7 said:**
> Sorry I was just about to reply, Im on a PC not a mac! I should have said OSX86 I guess.

One other thing - v important - my internet connection cuts off after about 4 mins browsing and I have to restart ubuntu to be able to use it again!

In that case, reboot your computer and enter the BIOS (the method varies, but you should see a quick message saying "Press <key> to enter setup". Keep hitting that key and you should get a menu. Go to the boot options and make sure the hard disk is set to boot first. Most motherboards will just jump straight to the hard disk if they can't find a bootable CD, but I've seen one or two machines which just give you an error.

---

### Post by Chrisp7 on 2007-02-28
I tried that too, didnt work either.

---

### Post by Chrisp7 on 2007-02-28
> **Tomosaur said:**
> In that case, reboot your computer and enter the BIOS (the method varies, but you should see a quick message saying "Press <key> to enter setup". Keep hitting that key and you should get a menu. Go to the boot options and make sure the hard disk is set to boot first. Most motherboards will just jump straight to the hard disk if they can't find a bootable CD, but I've seen one or two machines which just give you an error.

Hurrah! I tried that last night but it didnt work - it just worked finally - cheers!

edit - And finally the internet is working!? So strange why do things change like that!?

Thanks for your help guys:)

---

### Post by Chrisp7 on 2007-02-28
I spoke too soon!

I setup grub to be be able to selct the different OS's. then I tried to boot into Vista, I got this error message "A Kernal file is missing from the disk insert a system diskette and restart the system".
So I tried to remedy this with the Windows vista DVD, I wasnt able to, so I deleted Vista and reinstalled, great everything worked... But then I tried to get grub to select my OS's again, I booted up Ubuntu via the CD, in terminal typed:

sudo grub

then

find /boot/grub/stage1

and an error message came up : Error 15:File not found

So I though I would log in to Windows to look on the internet but lo and behold - "A Kernal file is missing from the disk insert a system diskette and restart the system". came again!

Please can someone help fix the Vista install and help load up grub again thanks:)

---

### Post by pxwpxw on 2007-02-28
if you have a separate /boot partition
then
grub> find /grub/stage1

should find it.

But thats not all, sounds like the MBR is being taken over by whichever
OS is installed last. i.e. ubuntu v/s the rest.

So if you can get ubuntu and grub running, then from ubuntu or the cd you 
should be able to sort out booting the others, without re-installing.

Do you have a floppy drive?

---

### Post by Chrisp7 on 2007-02-28
Thanks:)
No, but I have a USb drive and the motherboard is usb bootable.:)

edit- yes - it found grub with that search method -I assume I will get grub working again.

Vista might be the problem then

---

### Post by pxwpxw on 2007-02-28
if you can get ubuntu running again as per the link you posted, 
then stay in ubuntu and post your grub.conf (or menu.list).
Also you might be able to put grub onto your bootable usb, gives another
easier way to run grub. (like a grub floppy).

How were you booting the 3 OS's before installing ubuntu?

---

### Post by pxwpxw on 2007-02-28
You might need this - the full grub manual:

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

---

### Post by Chrisp7 on 2007-02-28
I cant even get Grub to boot up, I am basically back to square one - I can find grub in the terminal but it just wont boot on startup.

I have tried root (Hdx,x) and setup (hdx,x) and seems to work correctly in terminal but not on bootup (selecting only the hard disk to bootup in BIOS and in Gpart, both  flagging the boot partition as 'boot' and not as 'boot'.

---

### Post by pxwpxw on 2007-02-28
you should be doing
setup (hd0)
and it should give you some encouraging lines of  what it is doing.

if you want it to boot from the mbr when you restart the box.

---

### Post by Chrisp7 on 2007-02-28
Wont that overwrite the vista mbr? I will try it anyway:)

---

### Post by pxwpxw on 2007-02-28
Yes it will overwrite the MBR, but not Vista.

---

### Post by Chrisp7 on 2007-02-28
fantastic, it worked and grub works:) Also OSX86 will boot up via grub as does Ubuntu but I am still having problems with Vista and "a kernel file is missing" what did ubuntu do to it? Isnt there an easy way just to fix that Kernel error and it will all work fine then surely? (or is the Kernel error infact the fact that the MBR is controlled by grub?)

edit: and if I reinstall vista then I will need to re do grub boot and then I will have the same problem with the kernel again!

ps , here is my menu.lst buit it seems to work well so I dont think thats the problem.

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=57c275b5-284b-408d-8c2b-d492a0d9a3d7 ro
# kopt_2_6=root=/dev/sda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
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

title Vista install
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

title xp install
rootnoverify (hd0,2)
makeactive
chainloader +1
boot

title OSX install
rootnoverify (hd0,1)
makeactive
chainloader +1
boot

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,6)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,6)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd		/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by kittyhawk63 on 2007-02-28
> **Adramelech said:**
> I think you can only boot from primary partitions, try making a primary partition for ubuntu.

From my experience with GRUB, if you make one of your Windows' partitions primary, GRUB has to be loaded onto it. Otherwise, Adramelech is right. If you have GRUB on the Linux partition, Linux will have to be set as a primary. I'm fairly sure that you have to boot from the primary that has GRUB installed on it.

I am opened to being corrected. However, working with GRUB over several days, that is what I had to do to get it to work.

kh

---

### Post by Chrisp7 on 2007-02-28
grub seems to be working but I dont understand what it has done to Vista... anyone know?

---

### Post by pxwpxw on 2007-02-28
That menu.lst needs some thought, leave it alone and dont worry about vista until someone
can confirm where the vista boot loader is. I dont know, I dont have vista. The boot loader for XP is normally on the XP partition, not the MBR. May not be the case for vista.

Suspect vista may be using sectors immediately after the MBR, which can also be overwritten by grub-install for  stage1_5 and stage2.

There are ways to avoid that situation, but not simple.

Howeve, same problem should have shown up for anyone having vista/linux dual boot using grub.

I will have a closer look at the menu.lst. and what setup  does.

Any vista experts? Help.

---

### Post by pxwpxw on 2007-02-28
OK, after reading the manual, maybe this is the problem:

Background:

from the gnu grub manual:

[http://www.gnu.org/software/grub/manual/grub.html#chainloader](http://www.gnu.org/software/grub/manual/grub.html#chainloader)

[http://www.gnu.org/software/grub/manual/grub.html#OS_002dspecific-notes](http://www.gnu.org/software/grub/manual/grub.html#OS_002dspecific-notes)

> 
4.1.2 Load another boot loader to boot unsupported operating systems

If you want to boot an unsupported operating system (e.g. Windows 95), chain-load a boot loader for the operating system. Normally, the boot loader is embedded in the boot sector 
of the partition on which the operating system is installed.

   1. Set GRUB's root device to the partition by the command rootnoverify (see rootnoverify):

                grub> rootnoverify (hd0,0)
           

   2. Set the active flag in the partition using the command makeactive6 (see makeactive):

                grub> makeactive
           

   3. Load the boot loader with the command chainloader (see chainloader):

                grub> chainloader +1
           

      `+1' indicates that GRUB should read one sector from the start of the partition. 


But then:

> 
4.2.8 QNX

QNX seems to use a bigger boot loader, so you need to boot it up, like this:

     grub> rootnoverify (hd1,1)
     grub> chainloader +4
     grub> boot



Vista may have a bigger boot loader also, that would account for the 
grub message "a kernel file is missing" 

It may need similar treatment, should be safe to try
It should be safe to try chainloader +4 but only in the vista entry.
Make a backup copy of the menu.lst you have before any changes.
Save it to a usb stick or whatever.

[COLOR="DarkRed"]Then try this change, only for the vista entry in menu.lst.

```

title Vista install
rootnoverify (hd0,0)
makeactive
chainloader +4
boot


```
[/COLOR]

D**o not rerun grub setup. **

Just edit menu.lst and restart. 

[COLOR="DarkRed"]Alternately, and better, don't edit menu.lst at all, just restart and when the grub menu comes up, use the 'e' command to make a temporary change to the vista entry, as above - then continue to boot vista and see what happens.
[/COLOR]

 if +4 doesn't work try +8.

(This is only telling it to read a bigger file, may bomb, but should be harmless. No guarantees though.)

As a last resort if increasing the chainloader +n fails,
there is an additional option:

13.3.4 chainloader
&#8212; Command: chainloader [--force] file
If you specify the option --force, then load file forcibly, whether it has a correct signature or not. This is required when you want to load a defective boot loader.

[COLOR="DarkRed"]However I am having trouble understanding why this problem with vista has not
surfaced before - must be many such dual boot configurations with vista.
[/COLOR]
===================

---

### Post by pxwpxw on 2007-02-28
> **pxwpxw said:**
> OK, after reading the manual, maybe this is the problem:


[COLOR="DarkRed"]However I am having trouble understanding why this problem with vista has not
surfaced before - must be many such dual boot configurations with vista.
[/COLOR]
===================


Well that was an interesting theory of mine, but thats about all.

1. A search for < vista boot loader >  here and Fedoraa forum, finds many threads have had initial problems, but got vista + grub running, none have needed to change the chainloader +1 line, or caused problems by putting grub stages on the mbr.

 Micosoft knowledge base has articles about vista booting and multibooting.
 Bootrec.exe /FixMbr, will restore the MBR for vista ( overwrite the grub stage1 )

2.  One other point. Your menu.lst shows the 3 non-Linux entries inside the Default
 Options section, which is not where they should be. They should normally be down below the line: 

### END DEBIAN AUTOMAGIC KERNELS LIST
 Here.

---

