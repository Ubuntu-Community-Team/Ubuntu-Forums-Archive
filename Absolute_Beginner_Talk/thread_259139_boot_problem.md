---
title: "boot problem"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-16
Hi all!

I know it is my own fault for playing around with things, but I just can't seem to resist trying something new!!

I installed the latest Edgy Eft yesterday, just to see how it is coming along, it all went well until I tried changing some settings when it crashed and then wouldn't start again after rebooting.  That is not the problem, I deleted the partition it was on and reinstalled grub, but now Windows won't boot.  I can select it from the list and it looks as though it is booting but the little dotted line keeps running and nothing else happens!  I then tried reinstalling Edgy on the free space I have where I deleted it, but it wont do the partitioning bit.  

I also tried reinstalling Windows, but the Windows disc wont load.

So, if anyone knows what I have done wrong and if there is a fix for it, I would be very grateful.

I can still use Dapper, that is the only OS that will work at the moment.

Russty.

---

### Post by jordanmthomas on 2006-09-17
What dotted lines are you talking about?  The Windows boot screen or some GRUB screen?
If it's not getting to a Windows screen at all, maybe you could post your menu.list so we can have a look?

---

### Post by Russty of Oz on 2006-09-17
I mean the geen dots on the Windows screen as it loads.  What is the menu.list and how do I find it?

Russty

---

### Post by jordanmthomas on 2006-09-17
menu.list is here
```
/boot/grub/menu.lst
```
You don't need to post it, though.  The problem doesn't lie here:  it's a Windows problem
As soon as you select Windows from the GRUB menu, hit F8 until you see a menu come up.  From here, you can try:
1.  Last Known Good Settings  (hopefully this is all you will need)
2.  You can try safe mode to figure out what's wrong.

If you still can't get it going, someone may be able to help further.

---

### Post by Russty of Oz on 2006-09-17
I have tried those things and still nothing happens.  When I select Windows from the list of OS's a Windows screen appears saying that something is wrong because of some software changes I may have made (thats correct) and to insert the Windows disc and click repair.   But even the Windows disc won't start.  I must have done something wrong when either installing Edgy, deleting the Edgy partition or when reinstalling grub.

Russty

PS  I tried the menu.lst thing and it said "permission denied" ???

---

### Post by Skia_42 on 2006-09-17
just as a sidenote, Edgy EFT is still experimental so don;t count on support.

---

### Post by Frak on 2006-09-17
> **Russty of Oz said:**
> Hi all!

I know it is my own fault for playing around with things, but I just can't seem to resist trying something new!!

I installed the latest Edgy Eft yesterday, just to see how it is coming along, it all went well until I tried changing some settings when it crashed and then wouldn't start again after rebooting.  That is not the problem, I deleted the partition it was on and reinstalled grub, but now Windows won't boot.  I can select it from the list and it looks as though it is booting but the little dotted line keeps running and nothing else happens!  I then tried reinstalling Edgy on the free space I have where I deleted it, but it wont do the partitioning bit.  

I also tried reinstalling Windows, but the Windows disc wont load.

So, if anyone knows what I have done wrong and if there is a fix for it, I would be very grateful.

I can still use Dapper, that is the only OS that will work at the moment.

Russty.

Start up your computer with the windows disk in the drive- the windows installer will say it can't format the hard drive- it will then return to the command prompt- type D:\ -then WinNT -then Format C:\ (remember the :\ it is technically part of the name of the drive) once it is done formatting put in oemsetup, the windows installer should return to regular schedualed installing a useless OS.:)

---

### Post by jordanmthomas on 2006-09-17
It's not a command, it is a file, you can get its contents like this
```
cat /boot/grub/menu.list
```

Is your BIOS still set up to boot off a CD?  What goes wrong when you try to run the Windows CD?

---

### Post by Russty of Oz on 2006-09-17
> **jordanmthomas said:**
> It's not a command, it is a file, you can get its contents like this
```
cat /boot/grub/menu.list
```

Is your BIOS still set up to boot off a CD?  What goes wrong when you try to run the Windows CD?

When I put that in it said "no file or directory"

When I boot off the Windows CD it says to press any key to boot, then when I do it, it loads windows files and then the screen goes blank and nothing else happens.  

Russty.

---

### Post by confused57 on 2006-09-17
Try:
```
cat /boot/grub/menu.lst
```
The .lst is short for list.

---

### Post by Russty of Oz on 2006-09-17
Ok the menu.list worked that time.  This is what it says:  I dont know what those smiles are doing there, in the menu.list they are an 8 in brackets.

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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

russty@russty-desktop:~$

---

### Post by confused57 on 2006-09-17
Please post the output of:
```
sudo fdisk -l
```
The -l is a lowercase "L".

I'm not sure this will help any, your system not booting the Windows install cd may be a problem...does your Windows cd have any smudges or scratches on it?

---

### Post by Russty of Oz on 2006-09-17
russty@russty-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6378    51231253+   7  HPFS/NTFS
/dev/hda2            8095        9950    14908320   83  Linux
/dev/hda4            9951        9964      112455    5  Extended
/dev/hda5            9951        9964      112423+  82  Linux swap / Solaris
russty@russty-desktop:~$

No, it is a perfectly good disc.  If I put it in my other machine it wants to do its thing.

Russty

---

### Post by jordanmthomas on 2006-09-17
Thanks for posting menu.list, but it wasn't needed..

Can you boot off an Ubuntu CD on your broken system?

---

### Post by Russty of Oz on 2006-09-17
Yes, I can boot off a Ubuntu CD but cannot install it as it won't do the partition bit, I clicked the manual partitioning and also use the largest free space, but it just sits there!

Russty

---

### Post by jordanmthomas on 2006-09-17
Well, that makes no sense that you can't boot off your Windows CD.  
It's 1 am and I am tired, so I can't think.

---

### Post by Russty of Oz on 2006-09-17
Thats OK, thanks for trying to help.  

Russty.

---

### Post by confused57 on 2006-09-17
> **Russty of Oz said:**
> Yes, I can boot off a Ubuntu CD but cannot install it as it won't do the partition bit, I clicked the manual partitioning and also use the largest free space, but it just sits there!

Russty
I don't know what's going on, unless there is a problem with your cd drive...maybe some way to "clean" it, if that's the problem.

You might want to try booting up with the gparted live cd(approx 30 mb download):
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

If it boots up OK, you might be able to format the partition that Edgy was on as ext3 and gparted will also show your partition tables.

It's getting late for me also, I really wish I could help your more...but my computer & linux expertise is rather limited.
Keep us posted & Good Luck...

---

### Post by Russty of Oz on 2006-09-17
Well at least that worked, I formatted the empty section as ext3 and at least now I can install Ubuntu there.  I will have to wait until that finishes and then see if I can boot windows then.  If not, well, I guess it doesn't matter, who needs windows when you've got Ubuntu.

Russty.

---

### Post by Russty of Oz on 2006-09-17
Well, I had to format the windows partition and then it installed without a hitch.  

Thanks guys for the assistance. Much appreciated.

Now to see what else I can screw up!

Russty.:D

---

### Post by Russty of Oz on 2006-09-18
Now I have installed Windows and it worked well, then I reinstalled Ubuntu and that went OK too, but now when I boot I only get Ubuntu.  In the grub list it shows Ubuntu as the only OS.  On the Ubuntu desktop it shows windows as hda1 and I can see the windows files in there, so windows IS on the hard drive.  

So, how do I get windows listed in the grub menu?  I searched the forum and did the follow with no effect
           sudo grub
           find /boot/grub/stage1
           root (hd0,1)
           setup (hd0)
           quit

and Ubuntu is on hda2.

Russty.

---

### Post by Najand on 2006-09-18
Edit your /boot/grub/menu.lst using any editor, but with root privileges. (Like nano:
```

sudo nano /boot/grub/menu.lst

```

Add this at the end of it:
> title	Windows XP
root		(hd0,0)
makeactive
chainloader	+1


---

### Post by Russty of Oz on 2006-09-18
**EDIT:  I just did it with nano as you suggested and I found the list**.

There is nothing in the /boot/grub/menu.lst.

should I just put in what you suggested?  Also, do I type in "titile Windows 95/98/NT/2000" or do you just mean "Windows XP"

Russty

---

### Post by Najand on 2006-09-18
Huh? It is impossible for it to be empty...
Windows 95/98/ME/2000 is just the title... I thought you might have XP.

---

### Post by Najand on 2006-09-18
I hope you haven' changed the grub command settings.

---

### Post by Russty of Oz on 2006-09-18
What are grub command settings?  Anyhow, the windows bit is already in there just as you put it.  So does that mean it should work?  Because it doesn't.  Perhaps it is because it is windows Vista RC1? Maybe it doesn't recognise it?  It used to work before, it just showed up as windows XP.

:confused:

---

### Post by Najand on 2006-09-18
Well, it was the name we wrote there.... You can change it if you wish by editing /boot/grub/menu.lst 
What error did you receive? Can you just copy / paste the following command here?

```

[FONT="Arial Narrow"]sudo fdisk -l[/FONT]

```

---

### Post by petri on 2006-09-18
> **Russty of Oz said:**
> [B]EDIT:  ...

There is nothing in the /boot/grub/menu.lst.
...
Russty


Did you write with the last dot too? **menu.lst.**
In that case try whitout the last dot.

---

### Post by Russty of Oz on 2006-09-18
russty@russty-desktop:~$ sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6378    51231253+   7  HPFS/NTFS
/dev/hda2            8095        9950    14908320   83  Linux
/dev/hda4            9951        9964      112455    5  Extended
/dev/hda5            9951        9964      112423+  82  Linux swap / Solaris
russty@russty-desktop:~$

---

### Post by petri on 2006-09-18
> **Russty of Oz said:**
> ...
So, how do I get windows listed in the grub menu?  I searched the forum and did the follow with no effect
           sudo grub
           find /boot/grub/stage1
           root (hd0,1)
           setup (hd0)
           quit
...

Russty.

Did this while you were on Live-session?

---

### Post by Russty of Oz on 2006-09-18
Perhaps I should just be happy with Ubuntu.  After all, when the Vista trial runs out, I wasn't going to put windows in again as I prefer Ubuntu.  

If anyone can come up with a way of getting windows to work as well, I will try it.

Russty

---

### Post by Russty of Oz on 2006-09-18
> **petri said:**
> Did this while you were on Live-session?

Yes!

---

### Post by petri on 2006-09-18
Do it again, it has to work!

---

### Post by petri on 2006-09-18
Here you find quite a good GRUB-page: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Russty of Oz on 2006-09-18
> **petri said:**
> Do it again, it has to work!

Are you talking about the menu.lst ?

I think you must have missed the edit to the post where I said there was nothing in there, as I did try it again and I got the list.  

Sorry.

---

### Post by petri on 2006-09-18
Nope, I mean install grub

> So, how do I get windows listed in the grub menu? I searched the forum and did the follow with no effect
sudo grub
find /boot/grub/stage1
root (hd0,1)
setup (hd0)
quit

---

### Post by Russty of Oz on 2006-09-18
> **petri said:**
> Here you find quite a good GRUB-page: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I will check that out.  I just had a quick look at it and the Super Grub Disk looks like it might be the thing to try.

Thanks.  I will post what happens.

Russty

---

### Post by Russty of Oz on 2006-09-18
The Super Grub Disk did the job.   I am writing this from within Windows Vista so at least it does work.  I haven't read all the details of this Super Grub, but I think there is something there about how to get it dual booting, so I will read through it and work it out.

Thanks guys for the help. =D> 

Russty.:D

---

### Post by Russty of Oz on 2006-09-19
Hi all! :D 

Just an update to let those who have kindly helped me know what has happened.

The Super Grub disc got me into windows again, but at boot up time it still only showed Dapper.  So I thought I would format the ext3 partition and then install Edgy, and yes I know it is still an early testing version, and after installing Edgy, the boot list now includes Edgy AND Vista!!  And they both boot without a hitch.  So, I will play around with Edgy for a while and see how it goes, I know there will be bugs so I don't expect it to run flawlessly.  If the bugs get too much I will reinstall Dapper.

So all is fixed for now.

Thanks for the help.

Russty.:)

---

