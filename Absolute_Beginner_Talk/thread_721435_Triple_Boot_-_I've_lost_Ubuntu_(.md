---
title: "Triple Boot - I've lost Ubuntu :("
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by TpyKv on 2008-03-11
Good afternoon All!

I want to run a triple boot, with Vista, Ubuntu and Solaris Express Developer Edition...

I have had a dual boot with Vista & Ubuntu working fine, but now the problem comes with adding Solaris to it... I have lost the grub bootloader (replaced with the Solaris one) and Ubuntu is no longer an available option .

I installed Solaris after the linux swap, and can find resources telling me how to add the grub back after windows wipes it out, but nothing to help when Solaris wipes Ubuntu out!

I've tried booking the Ubuntu live CD, opening terminal and typed : 

sudo grub
>root (hd0,2)
>Setup (hd0)
>exit

but it does not execute the setup one - 

so I tried :

sudo gedit /boot/grub/menu.lst (Ubuntu Live CD)

but this is now a blank file....

I see the grub is now under Solaris, 

is there a way to get the grub back on the linux partition so I can see all three OS's ??

Thank you very much for reading....

---

### Post by bodhi.zazen on 2008-03-11
you need to restore grub just the same as with windows.

(Setup (hd0) is with a small s)

> setup (hd0)

And you have to run grub as root (sudo grub)

If you want to look at your ubuntu grub, fron the live CD, you need to mount it at say /media/ubuntu. It is then at /media/ubuntu/boot/grub/menu.lst

However, write down the solaris boot stanzas

OR, add this to the solaris /boot/grub/menu.lst :

Title Ubuntu
root (hd0,2)
chainloader +1
boot

This will bring up the Ubuntu grub. You can change the default and time out to 1 second. If you chainload you will not need to update grub every time you update the solaris or ubuntu kernel.

---

### Post by TpyKv on 2008-03-11
Brilliant, thank you very much!!

---

### Post by TpyKv on 2008-03-12
Hello again,

I added this to the Solaris bootloader : 

Title Ubuntu
root (hd0,2)
chainloader +1
boot

but it didn't work...

I think I have got the (hd0,2) part wrong, the thing is last night I tried every possible combination & still no luck...

I have taken the following info from gparted : 


unallocated		     1.47 GB
/dev/sda2	ntfs         118  GB
unallocated 		     5.74 MB
/dev/sda1 	ext3         7.63 GB
/dev/sda3       extended     1.91 GB
   /dev/sda5    linux swap   1.91 GB
 /dev/sda4      ext3         20.03 GB 
unallocated                  7.84 MB



And this is the print out from the Solaris grub : 

*************************************************************** (stars are added by me)

#pragma ident	"@(#)menu.lst	1.2	07/01/10 SMI"

#

# default menu entry to boot

default 0

#

# menu timeout in second before default OS is booted

# set to -1 to wait for user input

# timeout -1

#

# To enable grub serial console to ttya uncomment the following lines

# and comment out the splashimage line below

# WARNING: don't enable grub serial console when BIOS console serial

#	redirection is active!!!

#   serial --unit=0 --speed=9600

#   terminal serial

#



Uncomment the following line to enable GRUB splashimage on console

splashimage /boot/grub/splash.xpm.gz



#

# To chainload another OS

#

# title Another OS

#	root (hd<disk no>,<partition no>)

#	chainloader +1

#



title Ubuntu

       root (hd0,4)

       chainloader +1

       boot



# To chainload a Solaris release not based on grub

#

# title Solaris 9

#	root (hd<disk no>,<partition no>)

#	chainloader +1

#	makeactive

#

# To load a Solaris instance based on grub

# If GRUB determines if the booting system is 64-bit capable,

# the kernel$ and module$ commands expand $ISADIR to "amd64"

#

# title Solaris <version>

#	root (hd<disk no>,<partition no>,x)	--x = Solaris root slice

#	kernel$ /platform/i86pc/kernel/$ISADIR/unix

#	module$ /platform/i86pc/$ISADIR/boot_archive



#

# To override Solaris boot args (see kernel(1M)), console device and

# properties set via eeprom(1M) edit the "kernel" line to:

#

#   kernel /platform/i86pc/kernel/unix <boot-args> -B prop1=val1,prop2=val2,...

#

#---------- ADDED BY BOOTADM - DO NOT EDIT ----------

title Solaris Express Developer Edition 1/08 snv_79b X86

kernel$ /platform/i86pc/kernel/$ISADIR/unix

module$ /platform/i86pc/$ISADIR/boot_archive

#---------------------END BOOTADM--------------------

#---------- ADDED BY BOOTADM - DO NOT EDIT ----------

title Solaris xVM

kernel$ /boot/$ISADIR/xen.gz

module$ /platform/i86xpv/kernel/$ISADIR/unix /platform/i86xpv/kernel/$ISADIR/unix

module$ /platform/i86pc/$ISADIR/boot_archive

#---------------------END BOOTADM--------------------

#---------- ADDED BY BOOTADM - DO NOT EDIT ----------

title Solaris failsafe

kernel /boot/platform/i86pc/kernel/unix -s

module /boot/x86.miniroot-safe

#---------------------END BOOTADM--------------------


title Windows Vista 

	rootnoverify (hd0,1)

	chainloader +1



***************************************************************

I have ran sudo grub /media/ubuntu/boot/grub/menu.lst but again it's a blank document.

Can anyone please tell me where I'm going wrong - am I ever going to see Ubuntu again? 

:)

---

### Post by TpyKv on 2008-03-12
Anyone willing to accept a bribe?

 :lolflag:

The old saying - you don't know what you've got till it's gone - could not hold more truth...

I could live without Vista. But Ubuntu, well, It's a sad thought...

---

### Post by TpyKv on 2008-03-12
More details from fdisk -l


Device boot       Start         End          Blocks             Id       System
/dev/sda1         15597 	16592      8000370        83	    Linux
/dev/sda2	    192	15596      123731986     7        HPFS/NTFS 
/dev/sda3	    16593 	16841      2000092+      5        Extended
/dev/sda4 * 	    16842	19456      21004987+    bf       Solaris
/dev/sda5         16593 	16841      2000061       82       Linux Swap / Solaris

not sure if that will help anyone...?

---

### Post by glennric on 2008-03-12
Title Ubuntu
root (hd0,2)
chainloader +1
boot
That won't work to boot a linux kernel.  Try
```
title		Ubuntu
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```
Although you may have the wrong thing for (hd0,2).  I would guess that should be (hd0,0) from your fdisk output.  (hd0,2) is an extended partition.  Your root partition should be an ext3 (Linux) partition.

---

### Post by skroops on 2008-03-12
have you tried hd(0,0)?

---

### Post by bodhi.zazen on 2008-03-12
> **glennric said:**
> Title Ubuntu
root (hd0,2)
chainloader +1
boot
That won't work to boot a linux kernel.  Try
```
title		Ubuntu
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```
Although you may have the wrong thing for (hd0,2).  I would guess that should be (hd0,0) from your fdisk output.  (hd0,2) is an extended partition.  Your root partition should be an ext3 (Linux) partition.

No, chainload will boot grub from the Ubuntu partition. Chainloading is helpful in that one does not need to manually update grub (on Solaris) with every Ubuntu kernel update. You do need to install grub onto the Ubuntu partition (from Ubuntu) as well as the MBR (from Solaris). The other option is to use a /boot partition.

It looks like root is (hd0,0)

---

### Post by glennric on 2008-03-12
> **bodhi.zazen said:**
> No, chainload will boot grub from the Ubuntu partition. Chainloading is helpful in that one does not need to manually update grub (on Solaris) with every Ubuntu kernel update. You do need to install grub onto the Ubuntu partition (from Ubuntu) as well as the MBR (from Solaris). The other option is to use a /boot partition.

It looks like root is (hd0,0)

This is assuming that he has grub installed on his Ubuntu partition.  Is it installed there by default?  I don't believe that it is.

---

### Post by bodhi.zazen on 2008-03-12
> **glennric said:**
> This is assuming that he has grub installed on his Ubuntu partition.  Is it installed there by default?  I don't believe that it is.

You raise a good point, but it is easy to install grub to the Ubuntu partition.

/bodhi ponders writing a how to re: multi boot with a /boot partition or chainloading ...

---

### Post by glennric on 2008-03-12
> **bodhi.zazen said:**
> You raise a good point, but it is easy to install grub to the Ubuntu partition.

/bodhi ponders writing a how to re: multi boot with a /boot partition or chainloading ...

You should ponder that into action.  I think there are many out there that would benefit from that.

---

### Post by TpyKv on 2008-03-12
Skroops - yep, tried that, thanks...!


Nice one Glennric! 

Just tried it - it's not working - text as follows :

----------------------------------------------------------------

Booting command-list

root     (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel    /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro splash
          [Linux-bzImage, setup=0x1e00, size=0x1zcbb8]
initrd    /boot/initrd.img-2.6.22.14-generic 

Error 15: File not found

Press any key to continue...

----------------------------------------------------------------


Once again - any help / suggestions appeciated!!

---

### Post by TpyKv on 2008-03-12
bodhi.zazen - do it! :) 

thanks for your help yesterday, looking forward to seeing if between you two, I can stop pulling my hair out!

---

### Post by glennric on 2008-03-12
Is it possible that your root partition was on (hd0,2), and that partition was corrupted?  That could be why it now shows up as an extended partition.

---

### Post by bodhi.zazen on 2008-03-12
Well, I am sure there is more then one way to skin the cat.

What I advise :

1. Boot Solaris and change menu.lst back to chainload (as in my first post)

Ubuntu 
root (hd0,0)
chainloader +1
boot

2. Then boot the Ubuntu Live CD, fire up and install grub to the ubuntu partition :

```
sudo grub

> root (hd0,0)
> setup (hd0,0)
> quit
```

3. Reboot ...

When you select Ubuntu you should get a second grub screen , select Ubuntu a second time.

---

### Post by TpyKv on 2008-03-12
THREE CHEERS FOR BODHI.ZAZEN !!

Hip Hip, Hooooray!!!

IT WORKS!

(Sorry for the CAPS, I'm well excited!)

:guitar:

I'm not sure what to do with myself now. I might celebrate with a beer, or 10 :)

---

### Post by bodhi.zazen on 2008-03-15
> **glennric said:**
> You should ponder that into action.  I think there are many out there that would benefit from that.

Just for follow up, here is my how-to :

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

