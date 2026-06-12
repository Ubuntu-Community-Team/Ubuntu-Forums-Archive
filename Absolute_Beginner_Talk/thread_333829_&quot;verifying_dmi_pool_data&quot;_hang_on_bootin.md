---
title: "&quot;verifying dmi pool data&quot; hang on booting"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by dynacrylic on 2007-01-08
I'm running Kubuntu 6.10. The computer did an fast cold shutdown; now I'm unable to boot back into the OS.

When I boot from the hard disk, it boots into the bios screen than starts booting into the OS, but then reads:
Verifying DMI Pool Data......
Boot from CD: 
Boot from CD:

If I change the bois to only boot the the harddrive, rather than booting to a cd/dvd drive,  I just get:
Verifying DMI Pool Data......

I'm a little stuck here on how to resolve this problem. Any help would be appreciated (google was not help for me).

thanks in advance,

Erin- the shaken tired girl who wants her PC running before she goes to bed tonight

---

### Post by dynacrylic on 2007-01-08
still having problems... any help would be appreciated

---

### Post by MkfIbK7a on 2007-01-08
well sorry but i would actually suggest reinstalling...

---

### Post by dynacrylic on 2007-01-08
> **wert613 said:**
> well sorry but i would actually suggest reinstalling...

that's one suggestion I was hoping not to see :(

i've been trying to follow other stuff but I just can't get it going

---

### Post by MkfIbK7a on 2007-01-08
if you cant even get to grub i dont think you are going to have any hope of fixing it sorry :(

---

### Post by dynacrylic on 2007-01-08
> **wert613 said:**
> if you cant even get to grub i dont think you are going to have any hope of fixing it sorry :(

how would i fix grub? I've booted to the kubuntu 6.10 cd and mounted the disk. i'm in /boot/grub/menu.lst but I dont know what to change.

---

### Post by MkfIbK7a on 2007-01-08
there is nothing to fix in grub i just meant if you cant get past the bios...

post you grub lst here and i will try to help

---

### Post by dynacrylic on 2007-01-08
> **wert613 said:**
> there is nothing to fix in grub i just meant if you cant get past the bios...

post you grub lst here and i will try to help

I've been trying to use some info in this thread: [http://www.ubuntuforums.org/showthread.php?t=325490](http://www.ubuntuforums.org/showthread.php?t=325490)

I did "sudo fdisk -l" and this is what I got: 
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19175   154023156   83  Linux
/dev/hda2           19176       19457     2265165    5  Extended
/dev/hda5           19176       19457     2265133+  82  Linux swap / Solaris

Disk /dev/sda: 131 MB, 131252224 bytes
5 heads, 51 sectors/track, 1005 cylinders
Units = cylinders of 255 * 512 = 130560 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?     3051514     7528022   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(3051513, 1, 43)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(7528021, 3, 31)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      661528     8253796   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(661527, 2, 36)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(8253795, 0, 37)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?     7332869    14925136   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(7332868, 2, 24)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(14925135, 4, 28)
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?    11316397    11316615       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(11316396, 3, 20)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(11316614, 1, 30)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

I did "sudo mount /dev/hda1 /mnt/" and then got the /boot/grub/menu.lst:
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
# kopt=root=UUID=b70acb25-ce9e-413a-a6f6-923a30fb4366 ro
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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I tried changing the root (hd0,0) to root (hd1,0) but that didn't help, so I just replaced the modified file with the back I made before the chagnes.

---

### Post by Wim Sturkenboom on 2007-01-08
One of the suggestions that I found on the internet (source: [http://www.dewassoc.com/support/win98/verify_dmi_data.htm](http://www.dewassoc.com/support/win98/verify_dmi_data.htm) ):
>    1.  Apply power to the computer.
   2. Access the System BIOS.
   3. Disable both the Internal and External CPU Cache. These features are located in either the "BIOS Features" or "Advanced Settings" options of the BIOS Setup.
      NOTE: Consult the System or Motherboard User's Manual for exact location of the Internal and External CPU Cache settings.
   4. Save the BIOS changes and restart the PC to a System Boot Diskette. On startup, the screen should read:
          * Verifying DMI Pool Data
            Update Successful

            The system should continue booting normally.
   5. After the system successfully boots, re-start the PC and access the system BIOS.
   6. Enable the External CPU Cache. This feature is located in the "BIOS Features" or "Advanced Settings".
      NOTE: Consult the System or Motherboard User's Manual for exact location of the External CPU Cache setting.
      ! WARNING ! User's MUST re-enable this feature after resolving the problem for optimal system performance.
   7. Save the BIOS changes and restart the PC to a System Boot Diskette. On startup, the screen should read:
          * Verifying DMI Pool Data
            Update Successful

            The system should continue booting normally.

It's not said that it will work, so some other links:
google for [Verifying DMI Pool Data](http://www.google.co.za/search?hl=en&q=Verifying+DMI+Pool+Data&btnG=Google+Search&meta=)

---

### Post by dynacrylic on 2007-01-08
> **Wim Sturkenboom said:**
> One of the suggestions that I found on the internet (source: [http://www.dewassoc.com/support/win98/verify_dmi_data.htm](http://www.dewassoc.com/support/win98/verify_dmi_data.htm) ):

It's not said that it will work, so some other links:
google for [Verifying DMI Pool Data](http://www.google.co.za/search?hl=en&q=Verifying+DMI+Pool+Data&btnG=Google+Search&meta=)

Hung at "Verifying DMI Pool Data........ Update Successful". Rebooted and now back to "Verifying DMI Pool Data".

I had visited about half of those cites that were in that google result already before I posted on the forum.

Still trying to fix this.

---

### Post by dynacrylic on 2007-01-08
I don't want to reformat my hd again. Any other suggestions?

---

### Post by dynacrylic on 2007-01-08
Uhg... any more recommendations to get this back up and going?

---

### Post by marx2k on 2007-01-08
I really dont think this has much to do with your hard drive. You might wan tto check and make sure your CMOS Battery isnt dying?

Check the system time in your bios bootup and see if it's current with your current system time.

When I had this same problem, I went to the supermarket, purchased a new CMOS battery, installed and was up and running without problems.

---

### Post by dynacrylic on 2007-01-08
> **marx2k said:**
> I really dont think this has much to do with your hard drive. You might wan tto check and make sure your CMOS Battery isnt dying?

Check the system time in your bios bootup and see if it's current with your current system time.

When I had this same problem, I went to the supermarket, purchased a new CMOS battery, installed and was up and running without problems.

Swapped out the battery wiht one from a new motherboard. Now it's just hanging at "Verifying DMI Pool Data........ Update Successful"

---

### Post by marx2k on 2007-01-11
Have you considered updating or reflashing your BIOS firmware? 

Also, since youve reinstalled your battery, you may want to check to make sure all of your settings are  correct in BIOS. . especially the Plug And Play OS ECSD settings and things like that in BIOS. So youre saying it wont go past Update Successful, huh.. make sure your boot sequence is correct in BIOS. 

If you have time and a lot of coffee, you may want to do a few things (remove ALL extra hardware.. just leave a CD-Rom and the hard drive(s) -- see if that boots.  Also try moving the hardware to another motherboard to see if it boots from another mobo.

If you have more than one stick of RAM on that mobo, try booting with just one or the other in the SIMM slot.  Try a stick of RAM from another computer.

Basically, switch things up to see if you get anywhere.

---

### Post by angryfirelord on 2007-02-14
I was having a similar issue, except that it didn't stop, but kind of stalled for about 30 sec after displaying "Verifying DMI Pool data". Well, you have a couple choices (not in order):

1) The mbr is corrupted. Reinstall grub.
2) Revert back to dapper. I don't know why, but it worked for me.
3) Some setting is bad in your BIOS. Clear the cmos.
4) Check to make sure that all cables are connected firmly. Otherwise, your hard drive could be bad. In fact, remove the hard drive as one of the boot devices & disconnect it. See if it passes.

---

