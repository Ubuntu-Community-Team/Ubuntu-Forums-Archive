---
title: "crazy BIOS GRUB boot freakishnes"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-07-31
I'm finally booting in windows after installing ubuntu on an external YES!!! Finally!!! thank god! little files were lost, too. great. 

the problem:  how did this happen!? 

This is my Boot sequence under BIOS

[LIST=1]
[*]USB HDD: IC356090
[*]USB FDC
[*]IDE CD
[*]IDE HDD
[*]USB KEY:
[*]PC BEV: B02 DOO Yukon Pxe
[/LIST]

Okay....

Then I boot...
and it launches into the Pxe (LAST !! wtf???) sequence. and it shows the spindling DHCP "\" character while it never finds a server (what is Pxe? assuming it's a boot from a server),

 I press esc. OS not found.  

I press return.

then Finally. the grub menu that I've never seen before! 

and I choose the xp boot drive.


How did that happen? what happend?  how did I only access that menu after the Pxe attempt?  How can I fix this so I just boot the grub menu straightaway (which defaults to default drive after timeout)?

thanks.

---

### Post by kerry_s on 2007-07-31
did you make the usb partion bootable?
where is grub installed? sounds like it's in mbr, so you'd have to boot the ide first
you would have to use the alternate installer, to install grub to the usb, by typing in the path /dev/sda?, and it would need to be set bootable.

---

### Post by johntkucz on 2007-07-31
> **kerry_s said:**
> did you make the usb partion bootable?
where is grub installed? sounds like it's in mbr, so you'd have to boot the ide first
you would have to use the alternate installer, to install grub to the usb, by typing in the path /dev/sda?, and it would need to be set bootable.

hhhmmm...how would i know if it was bootable?

here's what I did.
I booted from livecd, installed ubuntu fiesty fawn into the external 8-gb hd in three partitions
sda1=home
sda2=/
sda3=swap

That's what I'm trying to find out: where is grub installed!!!!  What the hell -- where the hell is MBR?  in that file the solution lies, certainly.  


[HTML] sounds like it's in mbr, so you'd have to boot the ide first
you would have to use the alternate installer, to install grub to the usb, by typing in the path /dev/sda?, and it would need to be set bootable.[/QUOTE]
[/HTML]
what? what? your above post is gibberish, gobbledygook.  have no idea what that means and it lacks coherent english.

---

### Post by johntkucz on 2007-07-31
the menu.lst file I changed (when booted from live cd) resided here:
/media/sdd2_root/boot/grub/menu.lst


note: I mounted the 2nd partition (root partition) of ubuntu hd at sdd2_root

---

### Post by johntkucz on 2007-07-31
okay, first off. if you don't have answers to a posted question, don't "answer with questions" that's infuriating and moronic.  

That said YES YES YES !!! I Finally accomplished a dual boot!! FINALLY!  this is the first time boot in ubuntu from the external hd with xp installed on the internal hd.  Solid.

I've got a lot of questions to clarify how this worked.

What ARE the partitions listed in the menu.lst file (the one I changed)

I know windows_xp_me is the windows xp partition

but then there's a linux recovery and linux kernel and then a memtest.  how do those link up with my three linux partitions (swap, /, /home) on the external hd?  

What was that pxe thing?

where can I get more introductory info on menu.lst grub tweaking?

I have to know exactly how this happened so I can be sure to replicate it again if needed.

---

### Post by kerry_s on 2007-07-31
sounds like your your own best friend, try google if you want to learn.

---

### Post by johntkucz on 2007-07-31
> **kerry_s said:**
> sounds like your your own best friend, try google if you want to learn.

haha:):popcorn: briliant!  Thanks -- that's a true, sincere, poignant compliment right there.  In saying that, you just conveyed that I  possess (atleast a smidgen, hopefully more) of self-reliance, an incredibly valuable resources to me (and to emerson:) and to anyone trying to work with ubuntu!  I did an enormous amount of book writing (self-help millions of words, 5 books, subconsciously appeasing my parents goals, that nourished communication in ways, but i'm off that and digging OSes. but this computer stuff I'm finally reconnecting with and it is definitely MY stuff (some of it); it's infuriating as hell, but intriguing, and fun, and something you can feel devout, sincere, and loyal towards).  Exploring and learning about linux/unix file systems definitely rejuvenates long-time huge interests. 

Strangely, though, I always (sometimes only) unlike the own answers myself after posting to the board!!! Thanks

I FINALLY booted from external ubuntu and windows xp! 

I tweaked the "colors" feature of the menu.lst (purely just for celebratory hyper-nerd "kicks":KS), anyway to test that out without redoing a full reboot sequence.  That's very low priority.

Main questions:

Here's my fstab, finally, after booting from external ubuntu:
```
kooz@kooz-laptop:/media$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7944    63810148+  83  Linux
/dev/sda2            7945        9768    14651280   83  Linux
/dev/sda3            9769       10011     1951897+  82  Linux swap / Solaris

Disk /dev/sdb: 1021 MB, 1021312512 bytes
129 heads, 16 sectors/track, 966 cylinders
Units = cylinders of 2064 * 512 = 1056768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         967      997367+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(972, 128, 16) logical=(966, 57, 15)
kooz@kooz-laptop:/media$ 


```

What the heck is vmlinuz?
Why don't I see these (/dev/sda1,2,3  listed in the menu.lst file? What if I put them there?

I'll probably find answers to those on my own, but thanks a ton!

---

### Post by johntkucz on 2007-07-31
Some questions about my menu.lst  file

```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

default=0
timeout=15

title		[hd0,0]_windows_xp_me_
root		(hd0,0)
savedefault
makeactive
chainloader	+1


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
# kopt=root=UUID=3a79ad82-eb61-4d85-a3b3-08b8e5396b4a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

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



title		[hd1,1]_Ukernel_2.6.20-15_generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3a79ad82-eb61-4d85-a3b3-08b8e5396b4a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		[hd1,1]_Ubkernel+2.6.20-15_generic_RECOVERY_ROOTBOOT
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3a79ad82-eb61-4d85-a3b3-08b8e5396b4a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		[hd1,1]_Ubuntu+memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet
```

I renamed them funkily for troubleshooting
are
title		[hd1,1]_Ukernel_2.6.20-15_generic
and 
title		[hd1,1]_Ubkernel+2.6.20-15_generic_RECOVERY_ROOTBOOT

redundant, pointing to the same partition: their root is boot (hd1,1).  Also, shouldn't that be sda1 (which is what shows up in fstab for the external ubuntu drive?)

It works. that's great.  I need to know how menu.lst loads so I can troubleshoot it in the future (precautionary and curiously).

---

### Post by johntkucz on 2007-07-31
Nifty links for anyone following with similar quirks:

VERY lucid -- great intro -- explains everything
[http://www.howtoforge.com/working_with_the_grub_menu](http://www.howtoforge.com/working_with_the_grub_menu)

The menu.lst bible basically -- very confusing/cryptic.
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

also, maybe some previous freakishness of the boot working after the PXE boot was becaouse of some LILO stuff?
```
from a site:
Even if you stick with LILO as as your system's primary bootloader, a GRUB boot floppy at hand is the best and fastest way to get your system back, in the case your MBR went to be corrupted.
```

---

### Post by kerry_s on 2007-07-31
you crack me up.

> What the heck is vmlinuz?
[http://www.bellevuelinux.org/vmlinuz.html](http://www.bellevuelinux.org/vmlinuz.html)


> Why don't I see these (/dev/sda1,2,3 listed in the menu.lst file? What if I put them there?
wrong file> xedit /etc/fstab

---

### Post by kerry_s on 2007-07-31
whoo, slow down space questions please, i'm already seeing double. :)

---

### Post by johntkucz on 2007-07-31
> **johntkucz said:**
> 
redundant, pointing to the same partition: their root is boot (hd1,1).  Also, shouldn't that be sda1 (which is what shows up in fstab for the external ubuntu drive?)

It works. that's great.  I need to know how menu.lst loads so I can troubleshoot it in the future (precautionary and curiously).


The grub menu.lst menu-loader alwasy treats all hard disks-- (scsi, ide, internal, external, flash, etc.) regardles of what it's listed as under the files system table (fstab),like sda or something --  as hd. nifty to know.

But HERE's the craziness.  

The boot works . Great. Eureka! That's awesome.  I can boot from internal xp hd and external ubuntu hd, but HOW that happens is another story.

I seriously think the BIOS boot sequence display has inaccuracy.  Because the sequence says it to try internal first, but it jumps to something that causes the error 22.  If I manually select the boot drive every boot (external, internal, or cd), it works.  how can I fix this so it manually boots? by default to the menu.lst menu?  


Can't believe I was tweaking colors -- always drift into the superficial fun stuff - - when the core essential boot is still in progress.


here's the boot craziness.

Only attach external hd (if other external hds are attached, this doesn't seem to work).
2.  When BIOS v 83.01 kbc 608 load,s Manually select  the USB HDD.
3.  Black screen errors says OS not found
4.  Press Return
5.  grub menu.lst menu loads SUCCESS!

But WHAT in the hell is with all the 1-4 looniness?!

thanks.

---

### Post by johntkucz on 2007-08-01
The GNU Grub manual is very techy and succinct, but in its concision, the read can seem confusing.  

First off "foreground" color refers to the text and the 1pt border around the main box

the black backgroun is unchanged as is the white text below the box.  This is confusing because 
background color is really just "highlighted colors" with the foreground being the text and the background being the highlight box.  GNU Grub manual didn't supply those. (Can those be changed? probable, seeing that it's gnu open source, but that's a different game/angle possibly)

anyways

Normal:
 foreground refers to text, 1pt border
background refers to solid main rectangle

Highlight
foreground refers to highlighted text color
background refers to highlight selector recangle

Normal background is a constant once loaded.


Those specifics were implied and the grub manual is very confusing with that.

---
You can experiment with different color effects adding this to the menu.lst file (don't use red scare unless you know where the menu choices are located!)

```
# colortweaker
     title [light-green/brown blink-red/blue]
     color light-green/brown blink-red/blue

     title [red/brown blink-brown/blue]
     color red/brown blink-brown
	
      title [blink-brown/green blink-brown/blue]
     color blink-brown/green blink-brown/blue

     title [red/cyan black/cyan]
     color red/cyan black/cyan

     title [red scare]
     color red/red red/red

     title [red/red red/green]
     color red/red red/green


     title [black/green blink-magenta/light-gray]
     color black/green blink-magenta/light-gray

     title [blink-red/light-gray brown/cyan]
     color blink-red/light-gray brown/cyan
```

---

### Post by johntkucz on 2007-08-01
okay, 

made some progress on the boot sequence.
It automatically boots to the grub menu, which is awesome.  However, still dont' know what was going on with those previous BIOS kinks (the inaccurate sequence display). 


I usually to do everything myself -- eVERYTHING (unless it's ridiculously tedious and i already know how to do it)-- install OS, cooking food, learning subjects (all, philosophy, computers, programming, psychology, biology, neuroscience, etc.) -- I don't feel right unless I do that.  It's a very unique and strange tendency and interest.

---

### Post by confused57 on 2007-08-01
The Grub Section on this website is a little more "human readable"... everything you always wanted to know  about grub, and more:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by johntkucz on 2007-08-03
[QUOTE=kerry_s;3113509]you crack me up.


[http://www.bellevuelinux.org/vmlinuz.html](http://www.bellevuelinux.org/vmlinuz.html)



wrong file> xedit /etc/fstab[/QUOTE
I don't get it . what's so funny?  Just a guy figuring out this stuff on his own!  The own best friend thing definitely feels like the truth, though!  

I think I posted the file systems table code.  Ahhh!!:) so vmlinuz is like an "alias" of sorts for the kernel.  cool.  thanks for that awesome link.  

The linux information project looks like an interesting site -- concise, very minimalist, but seemingly complete of essentials.  looks like those "commands listed" should be the minimum known commands for any average CLIer!

---

### Post by johntkucz on 2007-08-03
I found a book by kier thomas -- brilliant, lucid and very informatiive.  It's been answering a lot of the key questions!

---

