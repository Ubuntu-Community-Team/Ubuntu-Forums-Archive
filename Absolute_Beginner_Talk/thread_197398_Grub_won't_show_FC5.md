---
title: "Grub won't show FC5"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-06-15
I just installed Fedora Core 5 into some freed space on my hard drive, and during the installation I selected "do not install grub" because I thought ubuntu's grub would recognize it. Well it doesn't, so how can it?
 
*****EDIT: Solution is at the bottom of the third page of this thread.

---

### Post by rai4shu2 on 2006-06-15
If you don't feel like editing the "menu.lst" by hand you can install grub as described here:

[http://forums.fedoraforum.org/showthread.php?t=112567](http://forums.fedoraforum.org/showthread.php?t=112567)

---

### Post by sgtBiafra on 2006-06-15
If you feel confident enough, you could edit /boot/grub/menu.lst manually. You could definitely add another entry for Fedora there.

I'm sure there is a better way but that's how I'd handle it.

**Edit:** doh! rai4shu2 beat me to it.

---

### Post by user1397 on 2006-06-15
[quote=rai4shu2] you can install grub as described here: [http://forums.fedoraforum.org/showthread.php?t=112567]("http://forums.fedoraforum.org/showthread.php?t=112567")[/quote]will the new grub not show my ubuntu os? 
[quote=rai4shu2]editing the "menu.lst" by hand[/quote]how exactly would I do that?

---

### Post by rai4shu2 on 2006-06-15
This thread has some more examples you could look at:

[http://forums.fedoraforum.org/forum/showthread.php?t=108117](http://forums.fedoraforum.org/forum/showthread.php?t=108117)

---

### Post by user1397 on 2006-06-15
btw, here's my /boot/grub/menu.lst file's os list:

title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-25-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-25-386
boot

title        Ubuntu, kernel 2.6.15-23-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin 
boot

can't i just delete the ones with kernel 2.6.15-23?

---

### Post by user1397 on 2006-06-15
will reinstalling fedora, but this time selecting to install grub, will my new grub see both ubuntu and fedora?

---

### Post by catlett on 2006-06-15
No, you'll have the samr problem with fedora's grub. You will have to add an ubuntu entry. You can easily add a fedora entry to grub. What partition is fedora on? If you're not sure, do a fdisk -l.
Post back the partition and I'll make up your entry for you.

P.S. You can quickly update grub and see if it detects fedora then before we edit the menu.Just run > sudo update-grub

---

### Post by user1397 on 2006-06-15
[quote=catlett]No, you'll have the samr problem with fedora's grub. You will have to add an ubuntu entry. You can easily add a fedora entry to grub. What partition is fedora on? If you're not sure, do a fdisk -l.
Post back the partition and I'll make up your entry for you.

P.S. You can quickly update grub and see if it detects fedora then before we edit the menu.Just run ```
sudo update-grub
```[/quote]the sudo update-grub didn't really do anything, it just left it as it was before.  down there, there's a pic of my partitions.  Fedora is on /dev/hda5 which is in /dev/hda4.  I don't know what u mean by "fdisk -l", I tried running it in the terminal, but it just took me back to $.

---

### Post by user1397 on 2006-06-16
oops double post

---

### Post by catlett on 2006-06-16
Sorry about that it's sudo fdisk -l and it shows your partitions.
Anyways you can make a generic entry in Grub's menu. It will prety much look like the windows entry.

```
title             Fedora Core 5
root             (hd0,4)
chainloader     +1
```

To add it to your list. Just run ```
sudo gedit /boot/grub/menu.lst
``` Go to the bottom of the list and add this entry. Save it and then reboot. Choose it and it should boot no problem.
If there is a problem, you can get specific. You can mount the fedora partition. If it isn't already you can mount it like this ```
sudo mkdir /media/fedora
``````
sudo mount /dev/hda5 -t ext3 /media/fedora
``` Open up the folder and open up the boot folder. This will have the "vmlinuz" (which will be the root entry and the "initrd" which will be the initrd image.) That is the information you use to make a specific grub entry where you list the kernel you want to boot and the initrd image.

Then you would put a kernel line in the fedora menu entry, as well as an initrd line.  This is my Fedora grub entry. If you have the same version kernel (vmlinuz)  then you can use this entry. If your vmlinuz is different, use  this as a termplate but put your version numbers in. Then do the same thing sudo gedit...  add this (or the entry that matches your kernel), save and reboot.
```
title                         Fedora Core
root                          (hd0,4)
kernel                        /boot/vmlinuz-2.6.16-1.2111_FC5
initrd                        /boot/initrd-2.6.16-1.2111_FC5.img
savedefault
boot
``` You don't have to remove any Ubuntu entries to put the FC5 entry in. You can have as many entries as you want in grub.

---

### Post by user1397 on 2006-06-16
okay Catlett, i've made tremendous progress obviously thanks to you, because following your advice, i was able to enter grub, select Fedora Core 5, and it said all that stuff up to "Uncompressing Linux..." but then it gave me this long list of errors and whatnot (this is the only part I can see, some of the other stuff is too far up the screen, so I can't view them, but here's the last part):


scsi0 : sata_via
ata2 : SATA link down (SStatus 0)
scsi1 : sata_via
Loading jbd.ko module
Loading ext3.ko module
Trying to resume from /dev/hda3

No suspend signature on swap, not resuming.
Creating root device.
Mounting root filesystem.
mount : could not find filesystem '/dev/root'
Setting up other filesystems.
Setting up new root fs
setuproot : moving /dev failed : No such file or directory
no fstab.sys, mounting internal defaults
setuproot : error mounting /proc : No such file or directory
setuproot : error mounting /sys : No such file or directory
Switching to new root and running init.
unmounting old /dev
unmounting old /proc
unmounting old /sys
switchroot : mount failed : No such fileor directory
Kernel panic - not syncing : Attempted to kill init!
[<c011a32e>]  panic+0x3e/0x170
[<c011cede>]  do_exit+0x71/0x6c8
[<c011d5b9>]  sys_exit_group+0x0/0xd
[<c0102bc1>]  syscall_call+0x7/0xb

That is the exact error message.

---

### Post by user1397 on 2006-06-16
Also, can i just shutdown and reboot my pc now?  or is it unsafe to do so?  (it is still showing the message from the above post.)

---

### Post by user1397 on 2006-06-16
Also, was i supposed to unmount fedora while in ubuntu, before trying to boot into FC5?

---

### Post by catlett on 2006-06-16
The error is not with mounting or unmounting. 
Let's make an exact path. The easiest way is to mount fedora and open the boot folder. Take a screenshot of Nautilus with fedora's boot folder open so I can see the initrd and vmlinuz.
From the screenshot I'll make an exact path for grub and then try booting. If there is an error then, your install might have been corrupted somehow.

Boot to Ubuntu. (If you ever get stuck with a bad boot like fedora it is O.K. to power off by cutting the power and then reboot) Mount Fedora and get a screenshot of the fedora boot folder.

I won't be back online for a couple of hours, I'm still at work.

---

### Post by user1397 on 2006-06-16
okay here's the screenshot

---

### Post by catlett on 2006-06-16
This is an exact path for grub. If this doesn't work then something might be wrong with your install of Fedora. Anyways put this entry in and reboot.
```
title           Fedora Core
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-1.2054_FC5
initrd          /boot/initrd-2.6.15-1.2054_FC5.img
savedefault
boot
```

If this doesn't work you have another option to multi-boot with ubuntu and Fedora. Copy your Ubuntu grub/menu.lst and print it or post it here. Install Fedora and let fedora install grub.
Once you boot into Fedora, edit the grub menu with your Ubuntu entry. That way you know the entry is the proper one for Ubuntu.
Hopefully you won't have to go that route.

---

### Post by user1397 on 2006-06-17
[quote=catlett]This is an exact path for grub. If this doesn't work then something might be wrong with your install of Fedora. Anyways put this entry in and reboot.
```
title           Fedora Core
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-1.2054_FC5
initrd          /boot/initrd-2.6.15-1.2054_FC5.img
savedefault
boot
``` 
If this doesn't work you have another option to multi-boot with ubuntu and Fedora. Copy your Ubuntu grub/menu.lst and print it or post it here. Install Fedora and let fedora install grub.
Once you boot into Fedora, edit the grub menu with your Ubuntu entry. That way you know the entry is the proper one for Ubuntu.
Hopefully you won't have to go that route.[/quote]okay, i tried that fedora entry, but to no avail.  it still gave me that error message.  i guess i'll try the last option.

---

### Post by user1397 on 2006-06-17
okay im keeping my menu.lst here:

title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-25-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-25-386
boot

title        Ubuntu, kernel 2.6.15-23-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin 
boot

title           Fedora Core
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-1.2054_FC5
initrd          /boot/initrd-2.6.15-1.2054_FC5.img
savedefault
boot

---

### Post by user1397 on 2006-06-17
It worked!  by adding my ubuntu grub entries into my new fedora-installed grub, i was able to boot into fedora OR ubuntu! thank you catlett, you made all of this possible.

*EDIT:  All users reading this thread:  look at the third page for my final solution before trying to reinstall fedora (which is quite drastic, I might add)

---

### Post by user1397 on 2006-06-17
Now there's just one more problem.  How can my new grub direct my ubuntu to boot automatically, instead of fedora?

---

### Post by user1397 on 2006-06-17
im sorry but....i gotta bump!

---

### Post by catlett on 2006-06-17
Hey, didn't see you. This is easy believe it or not. You can edit your menu again. Like this. 
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
[COLOR="Red"]default		0[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10 See the entry in red. That tells grub which entry to boot. So you can do this 2 ways. Either paste your Ubuntu entry to the top of the list. (Before Fedora's entry) Then Ubuntu will be 0. Or count down the entries to Ubuntu's and change 0 to the number. (remember grub counts 0 so 4 down the list is 3 to grub)
I would move Ubuntu to the top. Because if Fedora gets a new kernel, it will change the boot order and your Ubuntu entry will not be in the same spot.

Did I explain that good enough? If not repost.

---

### Post by user1397 on 2006-06-17
[quote=catlett] Did I explain that good enough? If not repost.[/quote]yes, you did! actually, it couldn't have been better! now ubuntu boots automatically.  Thanks for all your help, catlett.  

One final thing:  Can the fedora-installed grub  affect my ubuntu installation whatsoever?  How about when updating to a new version?  How could I then possibly reinstall ubuntu's grub?

---

### Post by catlett on 2006-06-17
Just keep a copy of your Fedora menu list somehwere. Now that you have the EXACT Grub generated entry for fedora, you can put that into ubuntu's grub if you ever upgrade and ubuntu's grub is installed.
You can even archive it by posting your fedora menu here. I get links to forum entries 3 and 4 years old so I assume the ubuntu server will stilll have this thread and your fedora entry saved in 6 months.

Gald it worked. Here's the grub manual if you ever want some light reading :razz: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by user1397 on 2006-06-17
[quote=catlett]Just keep a copy of your Fedora menu list somehwere. Now that you have the EXACT Grub generated entry for fedora, you can put that into ubuntu's grub if you ever upgrade and ubuntu's grub is installed.
You can even archive it by posting your fedora menu here. I get links to forum entries 3 and 4 years old so I assume the ubuntu server will stilll have this thread and your fedora entry saved in 6 months.

Gald it worked. Here's the grub manual if you ever want some light reading :razz: [http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html")[/quote]great suggestion, i think i'll post the fedora entry here, and in my home network, just to be double-secure.

---

### Post by user1397 on 2006-06-17
so for all you people that have been following this thread, instead of reinstalling FC5 with grub, first try editing ubuntu's grub menu by adding this entry:
 
title Fedora Core (2.6.15-1.2054_FC5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.15-1.2054_FC5 ro root=LABEL=/ rhgb quiet
initrd /boot/initrd-2.6.15-1.2054_FC5.img 
 

You would do this by typing in a terminal (applications > accessories > terminal): [LEFT]```
gksudo gedit /boot/grub/menu.lst
```[/LEFT]

 
then you would put this entry at the bottom of the OS list, it should look something like this:
 

[LEFT]```
# menu.lst - See: grub(8), info grub, update-grub(8)
```[/LEFT]
```

[LEFT]#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.[/LEFT]
 
[LEFT]## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0[/LEFT]
 
[LEFT]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3[/LEFT]
 
[LEFT]## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu[/LEFT]
 
[LEFT]# Pretty colours
#color cyan/blue white/blue[/LEFT]
 
[LEFT]## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret[/LEFT]
 
[LEFT]#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#[/LEFT]
 
[LEFT]#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST[/LEFT]
 
[LEFT]### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below[/LEFT]
 
[LEFT]## DO NOT UNCOMMENT THEM, Just edit them to your needs[/LEFT]
 
[LEFT]## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda1 ro[/LEFT]
 
[LEFT]## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)[/LEFT]
 
[LEFT]## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true[/LEFT]
 
[LEFT]## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false[/LEFT]
 
[LEFT]## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash[/LEFT]
 
[LEFT]## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single[/LEFT]
 
[LEFT]## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all[/LEFT]
 
[LEFT]## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true[/LEFT]
 
[LEFT]## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false[/LEFT]
 
[LEFT]## ## End Default Options ##[/LEFT]
 
[LEFT]title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-25-386
savedefault
boot[/LEFT]
 
[LEFT]title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.15-25-386
boot[/LEFT]
 
[LEFT]title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin 
boot[/LEFT]
 
[LEFT]title         Fedora Core (2.6.15-1.2054_FC5)
   root        (hd0,4)
   kernel     /boot/vmlinuz-2.6.15-1.2054_FC5 ro root=LABEL=/ rhgb quiet
   initrd       /boot/initrd-2.6.15-1.2054_FC5.img[/LEFT]
 
 

[LEFT]### END DEBIAN AUTOMAGIC KERNELS LIST[/LEFT]

```
 
 
 
then you could enter grub on startup, by pressing Esc, and you could select either ubuntu or fedora.

---

### Post by user1397 on 2006-06-17
oops bad post

---

### Post by rockballad on 2007-08-13
Thanks.

And here is the Fedora 7  booting info

```

root (hd?,?)
kernel /boot/vmlinuz-2.6.21-1.3194.fc7 ro root=LABEL=/ rhgb quiet
initrd /boot/initrd-2.6.21-1.3194.fc7.img

```

replace '?' with your own harddisk/partition info. The 'kernel' and 'initrd' can be different from yours, of course. So in Ubuntu, go to the partition Fedora installed, then go to /boot/grub and see the kernel and initrd to get the right version.

Have fun.

---

### Post by user1397 on 2007-08-13
> **rockballad said:**
> Thanks.
 
And here is the Fedora 7 booting info
 
```

root (hd?,?)
kernel /boot/vmlinuz-2.6.21-1.3194.fc7 ro root=LABEL=/ rhgb quiet
initrd /boot/initrd-2.6.21-1.3194.fc7.img

```
 
replace '?' with your own harddisk/partition info.
 
Have fun.thanks for the info, I've edited the first post of the thread to point people to these posts.

---

