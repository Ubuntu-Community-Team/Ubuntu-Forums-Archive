---
title: "Windows Failed at startup"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-04-03
Some one please help me, My wife is very mad with me at the moment.

Background story;

When I decided to try to use Ubuntu I was having problems with partitioning my Hard Drive. So I ended Up installing a third Hard Drive into my computer.

In order to be sure I didn't miss anything windows based up, I went and Physically unplugged two hard drives when I originally installed  Ubuntu. So under my boot heading in bios then it looked like this.

1  DVD Burner
2  CD-DVD Drive
3  150Gig with Windows operating system
4  250Gig with Photos/music
5  80Gig Ubuntu

What I would do would be every time I wanted to switch into or out of Ubuntu, I would come to the boot order in Bios, and just move the 80 gig up or down ahead of or behind the other two HD's. **I showed my Bride this incase I left it the wrong way she could get back to Windows.**

Trying to fix a mouse problem I ended up screwing Ubuntu up, so I did a full reinstall. This time However feeling more confident I left the other two Hard drives plugged in. So now when I start the computer a screen comes up asking if I want to us Ubuntu or Windows. How convenient!

I left my Bride a note explaining this, not knowing the next time she would try to make the switch would be at 4am **In the dark!** So not seeing the note she just goes to Bios and moves The 80 gig witch is now third in row in the boot order to the bottom of the list.

Up tries to Pop Windows but instead we get this Error on a Black Screen

Windows Could not start because the following file is missing or corrupt.
\Windows\System32\config\system
you can attempt to repair this file using the original setup CD-Rom select 'r' at the first screen to start repair.

What I am wondering is does anybody think this is related to the bride changing the boot order?
Does anybody think the Master CD is going to help?

I dont know if this helps but the start up menue screen asking wich one I want to run has 
2.6.17-11-generic as what I am running.

some one please help me and please advise me as to what to do. I can not even begin to tell yea how pissed the bride is going to be with me if I have to reinstall windows.

Thank you
Sabar

---

### Post by compmodder26 on 2007-04-03
Have you tried switching the boot order back to the way it was?

---

### Post by mikeyphi on 2007-04-03
> **compmodder26 said:**
> Have you tried switching the boot order back to the way it was?

I agree with the above!

Your system will look for the boot record on the drive specified in the BIOS bootlist... therefore having set up your system you must run it as set up... as suggested put the boot option back to what you had (before she changed it!)...and all should be OK!!!

---

### Post by hyper_ch on 2007-04-03
Don't worry.... just put the boot order back to the setting it was before and all will be fine :)

---

### Post by Sabar on 2007-04-03
I was pretty sure I had already put back the correct boot order. in fact, I was pretty sure I had already doubles checked it. But I just went and came back from checking the boot order again and Now I am rather sure its where I left it yesterday.

I guess I just have to put the master CD in and see what happens.

I just wish I knew if this was related to me or the bride screwing something up, or if this is just something that happened all on its own and picked a very convenient time to do it.

---

### Post by confused57 on 2007-04-03
I agree with the advice already given to you, set the bios boot order back to the way it was when you reinstalled Ubuntu:
1 DVD Burner
2 CD-DVD Drive
3 150Gig with Windows operating system
4 250Gig with Photos/music
5 80Gig Ubuntu

If you want Windows to automatically boot unless you select Ubuntu, copy & paste your Window's entry just above the ###BEGIN AUTOMAGIC KERNELS LIST, similar to what's described here:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

You would use your Window's grub entry, but Windows would boot automatically each time.

---

### Post by mikeyphi on 2007-04-03
> **Sabar said:**
> I was pretty sure I had already put back the correct boot order. in fact, I was pretty sure I had already doubles checked it. But I just went and came back from checking the boot order again and Now I am rather sure its where I left it yesterday.

I guess I just have to put the master CD in and see what happens.

I just wish I knew if this was related to me or the bride screwing something up, or if this is just something that happened all on its own and picked a very convenient time to do it.

Before you do anything too drastic!  Just try booting your system from the 80G drive and then the 150G drive.
Do you see the boot menu at all?

---

### Post by Sabar on 2007-04-03
I am going to go and move things around in Bios one more time.

I know I am a bit confusing let me explain this part a little better.
1 DVD Burner
2 CD-DVD Drive
3 150Gig with Windows operating system
4 250Gig with Photos/music
5 80Gig Ubuntu

That is how It looked the first time I installed Ubuntu after removing my other two hard drives.

Then I reinstalled Ubuntu, but I left the other two drives connected so it looked like this right up till this morning when she changed it

1 DVD Burner
2 CD-DVD Drive
3 80Gig Ubuntu
4 150Gig with Windows operating system
5 250Gig with Photos/music

and the Grub? has been working fine. in fact now that I have them back to this order it is working fine again. But I still have this error when restarting Windows

> \Windows\System32\config\system

I don't know if this is all related or not. maybe Windows just picked a bad time to freak out.

The way I even learned about the grub was when I got my mouse working and had to restart Ubuntu. So I restarted with out going to Bios and this screen comes up asking which operating system I want. Gotta say I Like it! its alot better than going into bios again.

thanks for the help guys 
Sabar

---

### Post by Sabar on 2007-04-03
Oh oh. ah, I think maybe I am getting confusing. 

Yes I have the boot menu now.

If I restart right now it will open the boot menu first

then, from the boot menu, I go to open windows

and I get the message

> Windows Could not start because the following file is missing or corrupt.
\Windows\System32\config\system
you can attempt to repair this file using the original setup CD-Rom select 'r' at the first screen to start repair.

That is my problem, this error.

Looks like the only thing I can do is put the resource CD in and try to fix it. I just wanted to make sure no one else here had a better idea.

I don't know if this is even related to the bride changing Bios or not, it may have just happened on its own. I have never seen this happen before, but it just may be a coincidence.

Thanks for all the posts though. They have been helpful
Sabar

---

### Post by confused57 on 2007-04-03
You might want to post your menu.lst entries to boot Ubuntu & Windows, as well as:
```
cat /boot/grub/device.map
```

You may end up booting up the Window's install cd, enter recovery mode(press "r"), then enter FIXBOOT...post the output of the above commands, hopefully we can get your Windows booting again with grub.

Added:  Can you boot your Window's drive, by selecting it in bios as the first hard drive booted?

---

### Post by Sabar on 2007-04-04
Even when I boot from the windows drive I still get the same error message. 

thats part of why I am not sure if this all started from changing the boot order in bios. 

I am getting the black screen with the option of booting either windows or Ubuntu. that seems to be working then I get the above mentioned error. weather I go thrue what I am assuming is grub, or just changing bios to boot from the windows Hard drive.

just kinda nervous about putting the master CD to see if that can fix it :( 

Probably should just try that.

---

### Post by confused57 on 2007-04-04
> **Sabar said:**
> Even when I boot from the windows drive I still get the same error message. 

thats part of why I am not sure if this all started from changing the boot order in bios. 

I am getting the black screen with the option of booting either windows or Ubuntu. that seems to be working then I get the above mentioned error. weather I go thrue what I am assuming is grub, or just changing bios to boot from the windows Hard drive.

just kinda nervous about putting the master CD to see if that can fix it :( 

Probably should just try that.

Since you can't boot when the Window's drive is selected first in bios, you might need to boot up the Window's installation cd(not a recovery cd), press "r", then FIXMBR & you may also need to run FIXBOOT.

Before you do this, if you can still boot into Ubuntu, is to download the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
probably take you all of 10 minutes to download & burn to cd(maybe a cd-rw that you have lying around).
if the SGD isn't able to boot Windows, then you probably need to use the recovery console from the install cd.

---

### Post by Sabar on 2007-04-04
First and for most I want to thank you so very much on helping me with this. at this point I am so lost I dont know what I am doing.

Ok, out of desperation before I read your last post I put my AlienWare Microsoft Windows XP home edition system recovery CD-Rom in.

First thing I don't understand is, my computer is supposed to boot from cd-rom first before anything else. well it didn't, the first thing up was the screen asking if I wanted to load Ubuntu or Windows. ( thats the Grub, right? )

Ok so I went in and Physically unplugged my Ubuntu Hard drive both from the PCI card and the Power. Never can be to sure.

after doing that, on restart, I got a quick flashing saying to press any key to start disk. took me a few tries do to having only a second to do it.

then the disk started loading and the next screen I saw said this.
> 
Windows XP home Edition Setup

The following list shows the existing partitions and the unpartioned space on this computer.

us the UP DOWN keys to select an item in the list.

*To set up windows XP on the selected item press enter.
*To create a partition in the Unpartitioned space, press C.
*To delete the selected partition, Press D.

157066 MB Disk 0 at ID 0 on bus 0 on atapi [MBR]

F: Partition1 [NTFS]                                        157057MB <136318 MB Free>
    Unpartitioned space                                   8MB

238473 MB Disk 0 at ID 0 on Bus 0 On atapi [MBR]

G: Partitioned [NTFS]                                      238473 MB <173157 MB Free>

Unknown Disk
  <There is no disk on this drive>


Enter=Install         D=Delete Partition          F3=Quit

From what I Google showed me, I was expecting my first screen to have an R option
Gotta say now I am completely befuddled.

another thing My disks are normally labeled C, and D, Respectively. why is it calling them F, and G?

Just how bad are things messed up.

after I post this I am on my way to download super Grub as I was told to do.is there anyway i can get an explanation as to why?

Like I said I am really at a loss for everything right now.

Thanks again guys you have been great
Sabar

---

### Post by confused57 on 2007-04-04
About the only thing you can do with a recovery cd, from what I've read, is a complete reinstall of Windows...you'd need to borrow a Window's install cd to perform a FIXBOOT.
The Super Grub Disk is able to boot Windows(if it is bootable) and it can also restore your Window's drive mbr(essentially do the same thing as fixmbr).  Try SGD and see if you can boot Windows...if it doesn't see below.

I don't know if it'll help or not, but connect all your drives back the way they were when you installed Ubuntu.  Sounds like you're able to boot into Ubuntu...if you can, open a terminal(Applications---Accessories---Terminal), enter(copy & paste) the following:
```
sudo fdisk -l
```
the -l is a small "L"
this will show your partition tables on your hard drives

```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list
you really just need to post the entries to boot Ubuntu & Windows

```
cat /boot/grub/device.map
```

I know you already have, but verify in bios your hard drive boot order.

Post  the output of the above and hopefully someone will see a problem that can be corrected without having to reinstall Windows.  I won't be able to follow your progress for several hours, I need to get a little shuteye, it's going on 3:30 AM here and past my bedtime.
Good luck....there's plenty of other very knowledgable people in the forum who might see something in your outputs and may be able to point out something else you need to post.

---

### Post by Sabar on 2007-04-04
Thank you very much confused57. Yea I am an east coaster also getting time for bed. I just wish I knew what caused this problem in the first place.

thanks I will give this all a try in the morning

Sabar

---

### Post by confused57 on 2007-04-04
Ubuntu & Linux has a habit of keeping me up 'til the "wee" hours of the morning...just thought of something before bed, in case it becomes inevitable that you're going to have to reinstall Windows, hopefully not, you may already know you can use Ubuntu to recover files(not programs, except .exe files) from your Windows.
See the first link in my signature, check out the "Mounting..." section & there's also some good info on grub & bootloaders.

Here's the section for mounting your Window's NTFS partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)
the instructions are for the live cd, but work just as well with an installed Linux.

See you later, with good news I hope.

---

### Post by Sabar on 2007-04-04
THANK YOU that may keep the bride from killing me!

---

### Post by ndefontenay on 2007-04-04
I'm an east-side-of-the-earther and taking relay.

What kind of files does your wife need on windows.
As a matter of fact, she could be able to use Linux herself if she could access the files she wants, right?
Maybe it's the right time to convert her!

Good luck with the repairs. Let us know the outcome so we can keep helping.

---

### Post by Sabar on 2007-04-04
I am just learning Ubuntu my self. Gonna be kinda hard to convert her right now. ;-)
I have some things to try here then I'll let yea know how it turns out.

Sabar

---

### Post by Sabar on 2007-04-04
Ok tried to install Super Grub. I just want to say for the record. yea its posable to screw up the best of directions.

this link is to the post on screwing up Super Grub

[Grub>]("http://ubuntuforums.org/showthread.php?t=401274")

I gotta get to work, try it again tonight after midnight.

you know, from what I am reading and seeing I am starting to think the problem is with Grub.  Ok, how many people just slapped their heads? 

well duty calls gotta get going
Sabar

---

### Post by Sabar on 2007-04-04
This is the output confused57 said to post a while back to see if some one see's something wrong here. its long!

:confused: 
alien@alien-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20022   160826683+  44  Unknown

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001   44  Unknown

Disk /dev/hde: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        3497    28089621   83  Linux
/dev/hde2            3498        3649     1220940    5  Extended
/dev/hde5            3498        3649     1220908+  82  Linux swap / Solaris
alien@alien-desktop:~$ 



:confused: 
alien@alien-desktop:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=4ac95ccc-431f-4b78-906f-3533c73efb0c ro
# kopt_2_6=root=/dev/hde1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hde1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hde1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hde1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hde1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

alien@alien-desktop:~$ 


:confused: 
alien@alien-desktop:~$ cat /boot/grub/device.map
(hd0)   /dev/hde
(hd1)   /dev/sda
(hd2)   /dev/sdb
alien@alien-desktop:~$ 


Does this help at all? and what does it all mean?
thanks guys for being so helpfull and paitient with me
Sabar

---

### Post by confused57 on 2007-04-04
The command outputs you posted all look good, except the filesystem on sda & sdb are not recognized...I wonder if a setting in your bios has changed to cause this, maybe they were accidentally reset in a raid configuration.  That might be something you may want to check into, just changing the boot order in bios shouldn't affect your ability to boot Windows.  You were able to boot Windows OK before this?

You probably should try burning another copy of the Super Grub Disk, I don't know what happened for it to give you a grub prompt.

Added:  I don't know what settings to check in bios, but there may be someone more experienced  in the "Hardware..." section who might know.  You could start a new thread, making the title descriptive of your problem, maybe something like "SATA filesystems unknown, bios configuration problem?" or something to that effect.  Give a short summary of how your problem started & link to this thread, may want to post your "sudo fdisk -l" output in the new thread so someone immediately knows what you're seeing.

---

### Post by Sabar on 2007-04-07
Problem Is some what resolved. I got a copy of Windows and the system Restore worked.
Rather Happy I did not have to reinstall all of windows. Well let me put it this way the bride is happy ;-)

Sabar

Thank you everyone for your responses I can not begin to explain how helpful every one has been.

---

