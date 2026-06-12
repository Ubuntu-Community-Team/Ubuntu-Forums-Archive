---
title: "GRUB corrupted for some reason after reboot"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by faraazs on 2006-12-13
I am not sure what I did but GRUB is really messed up. I rebooted my computer to see if the secondary hard drive would mount and I was presented with a message of GRUB error 15 when the computer tried to start up.

I've searched for the error on the ubuntu forums and tried to reinstall GRUB off of the live cd, but that didn't help. I even backed up all of my files onto the secondary hard drive and tried to do a clean install with erasing the disk completely, but that didnt help either. The system keeps booting up with the error of grub error 15.

Any help in this situation?

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9447    75882996   83  Linux
/dev/hda2            9448        9729     2265165    5  Extended
/dev/hda5            9448        9729     2265133+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161   83  Linux
ubuntu@ubuntu:~$ 
```Since posting this, I've tried multiple things... For example, I saw that both drives had the boot flag so I kept it only on the drive that was going to be used when booting (the master drive). I tried reinstalling grub again with the method described in [this]("http://ubuntuforums.org/showthread.php?t=224351") thread.

I'm out of ideas now...can anyone shed some light into how to fix this problem?

---

### Post by faraazs on 2006-12-13
Ugh...I've been working on this for hours...and still no success. Can anyone help me with this?

---

### Post by ciscosurfer on 2006-12-13
This page may be of assistance: [http://tinyurl.com/yaqotu](http://tinyurl.com/yaqotu) 

It describes how to reinstall GRUB (you can ignore the Windows part).

---

### Post by louieb on 2006-12-13
Do I have this right? You had Ubuntu up and running. Then you shut down the computer and added a second hard drive, and rebooted.   
According to [documentation I trust]("http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable") Error 15 is a file not found error. That is very strange I don't know why installing another drive would cause that. And I really don't understand why a reinstall did not fix it. 
Are You sure your master slave setting are alright? 
Do you get to the grub menu?

---

### Post by faraazs on 2006-12-13
Thats mostly correct. Except that I had my previous drive installed and ubuntu recognized it and was even able to mount it. It's also in ext3 format with just 1 partition for storage purposes. Everything had been going fine... I am not sure what I did but when I rebooted, GRUB died :(.

I've been going on and off the live cd lately and moving my backup files from hda to hdb and all that to try to reinstall ubuntu on hda (master) multiple times but GRUB still wont fix itself.

I'm pretty sure my configuartion is right since it was working before and booted into the master before...I haven't changed anything since then in terms of hardware.

---

### Post by bulldog on 2006-12-13
Can you provide us a copy of your menu.lst?

---

### Post by faraazs on 2006-12-13
```
ubuntu@ubuntu:~/hda/boot/grub$ cat menu.lst
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
timeout         3

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
# kopt=root=UUID=d40dffe7-2d1c-4a89-84b3-77d6f3199d26 ro
# kopt_2_6=root=/dev/hda1 ro

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~/hda/boot/grub$ 

```

---

### Post by louieb on 2006-12-13
OK well from you fdisk hda looks like a normal let Ubuntu do its thing with the whole drive install. 
Now for a little trouble shooting. 
The problem is one of two things.[LIST=1]
[*]grub is not loading. or
[*]it did load and it can't boot Ubuntu.[/LIST]Press the esc key when grub first start loading and see if that brings the menu up.  If the menu comes up thats good.  and it means the problem is in the file menu.lst. 
If it does not come up then the steps you have already done is what I would say do next. Since you have already done them I am at this point lost.  

If you get a grub menu get back and I'll walk you through how to fix it. 
Please post the content of the file menu.lst.
and post the output from the ls command for 2 directories.
/boot
/boot/grub
 
Lets check for the following files.
i[COLOR=DarkRed]n the /boot directory [/COLOR]
abi-2.6.15-26-386     
initrd.img-2.6.15-26-386  
System.map-2.6.15-26-386
config-2.6.15-26-386
vmlinuz-2.6.15-26-386
Your version # may vary but the number part of the name(s) should all be the same.
i[COLOR=DarkRed]n the /boot/grub directory.[/COLOR]
device.map 
stage1   
stage2
menu.lst
Oh hi Bulldog. I was just going to ask for the menu.lst but I see you got him to post it.

---

### Post by bulldog on 2006-12-13
Nothing wrong with that.

But you stated you reboot to see if your second hard disk would be mounted.
Can you explain the reboot?
If it was up and running why couldn't you just take a look in fstab or in /media to get that information.

You did probably something which made a reboot necessary,I like to know what you did.:D

---

### Post by faraazs on 2006-12-13
Firstly, I'd like to thank everyone for the help. I really appreciate it. Hopefully we can get to a solution soon...

Secondly, the reason I rebooted was to see if ubuntu would automatically mount the harddrive after I added it to the fstab since its a pain mounting it by hand every single time. This is the last thing I remember doing before the problem occured since I rebooted to see if it would automount. This may or may not have been the reason though.

What I can't understand is why GRUB is misbehaving even though all configurations are correct. Even with a complete system reinstall from the live cd which should overwrite the boot folder and reinstall GRUB, I still get the same error.

In my second harddrive (hdb), there are no GRUB files, simply a lost+found folder and a backups folder which contains my backups. I am thinking that the system is somehow defaulting to that disc to read the boot sequence or something and cant find the files there which returns the GRUB error 15.

Any further ideas?

---

### Post by bulldog on 2006-12-13
Did you try ```
sudo update-grub
```

It's rather strange,a new install and the same error.
Are you sure on which disk GRUB is installed?
It happens GRUB has another way of deciding which drive is (hd0).
If you disconnect the second disk,you still se the grub menu?

Just some shot's it the dark though.:(

---

### Post by faraazs on 2006-12-13
That worked! For some reason, GRUB always wanted to load files from the slave harddrive which was my backup drive! It all makes sense now...the reason why it stopped working was because I removed all files except the lost+found folder from the slave drive because I was going to use it as a drive for keeping my backups.

It works perfectly with only one drive in it meaning that for some reason it is selecting the slave drive first to find GRUB. Earlier in the thread, someone suggested to use the Super Grub Disk and when I tried it, it also selected the slave drive.

My solution is to just keep the boot folder for grub on the slave drive so that it can boot until I can figure out how to change which drive GRUB selects first...

Thanks for all of your help Bulldog! I really appreciate it.

---

