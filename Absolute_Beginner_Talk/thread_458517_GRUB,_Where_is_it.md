---
title: "GRUB, Where is it?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Straft on 2007-05-29
I just installed ubuntu 7.04, and GRUB didn't come with it? I've got a another drive with Windows on it and I need to be able to boot up into Windows when I want. Any idea how to fix this?

---

### Post by dbbolton on 2007-05-29
i had a similar problem once. this thread will give you instructions on how to re-install GRUB:

[http://ubuntuforums.org/showthread.php?t=320216](http://ubuntuforums.org/showthread.php?t=320216)

---

### Post by mikewhatever on 2007-05-29
To answer the first question, read this page [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
It should explain most of the things you want to know about grub.

> just installed ubuntu 7.04, and GRUB didn't come with it?
What do you mean by that? Can you boot into Ubuntu? If yes, try pressing Esq key during the start up. What happens when you turn on the computer.

---

### Post by Straft on 2007-05-29
> **mikewhatever said:**
> To answer the first question, read this page [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
It should explain most of the things you want to know about grub.


What do you mean by that? Can you boot into Ubuntu? If yes, try pressing Esq key during the start up. What happens when you turn on the computer.

Ok well now I just found out it's a different problem, I didn't notice grub was there. Timer goes by so fast. Anyway, it's not detecting my other drive. Just shows Ubuntu, but not Windows.

How do I make it detect my other drive?

---

### Post by mikewhatever on 2007-05-29
You can prolong the timer using the link I posted above.
Can you also post the outputs of the following commands from Application>Accessories>Terminal
> cat /boot/grub/menu.lst
> sudo fdisk -lu

---

### Post by Straft on 2007-05-30
> **mikewhatever said:**
> You can prolong the timer using the link I posted above.
Can you also post the outputs of the following commands from Application>Accessories>Terminal

Ok I did that, but I GRUB has no Windows boot option. It's not detecting my windows drive :|

---

### Post by confused57 on 2007-05-30
> **Straft said:**
> Ok I did that, but I GRUB has no Windows boot option. It's not detecting my windows drive :|
You really need to post the output of:
```
cat /boot/grub/menu.lst
```
until you do, it would only be a guess as to what your Window's entry should be.

---

### Post by pnix on 2007-05-30
you can add window menu manually in /boot/grub/menu.lst [if you know where is your windows partition]
here is example, add this to menu.lst. 

```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

root (hd0,0) means first harddisk,partition1 e.g. hda1

---

### Post by drowner on 2007-05-30
> **pnix said:**
> you can add window menu manually in /boot/grub/menu.lst [if you know where is your windows partition]
here is example, add this to menu.lst. 

```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

root (hd0,0) means first harddisk,partition1 e.g. hda1

But, we don't know that his/her windows partition is on hd(0,0), so I wouldn't post advice until you have seen the menu.lst and an fdisk -l. Take care when giving advice.

Straft, post the output of the commands given by mikewhatever. The first one shows the contents of grub's menu.lst file, which tells grub which operating systems exist, and where they are.

The second one shows us which partitions and drives linux can see, so we can identify which one is your XP partition, and modify the menu.lst accordingly

---

### Post by Straft on 2007-05-30
Ok heres the output...

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
# kopt=root=UUID=8fdda744-8841-4f9a-b3e8-f7d8c6702a64 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=8fdda744-8841-4f9a-b3e8-f7d8c6702a64 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=8fdda744-8841-4f9a-b3e8-f7d8c6702a64 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=8fdda744-8841-4f9a-b3e8-f7d8c6702a64 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=8fdda744-8841-4f9a-b3e8-f7d8c6702a64 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Inxsible on 2007-05-30
Your menu.lst says that you do have Windows XP in the GRUB. Its the very first one !!
 
Cant you boot into XP ?

---

### Post by Inxsible on 2007-05-30
Also, how about the output of 
```
sudo fdisk -l
```
 
-l is a lowercase L

---

### Post by haricharan on 2007-05-30
> **Straft said:**
> 

```


title           Microsoft Windows XP Professional
** root            (hd0,0)**
savedefault
makeactive
chainloader     +1

title           Ubuntu, kernel 2.6.20-16-generic
** root            (hd0,0)**
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=8fdda744-8841-4f9a-b3e8-f7d8c6702a64 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
** root            (hd0,0)**
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=8fdda744-8841-4f9a-b3e8-f7d8c6702a64 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
** root            (hd0,0)**
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=8fdda744-8841-4f9a-b3e8-f7d8c6702a64 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
** root            (hd0,0)**
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=8fdda744-8841-4f9a-b3e8-f7d8c6702a64 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
** root            (hd0,0)**
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I believe you have overwritten your Windows...and you might have to start from scratch again.... The Windows and Ubuntu kernels are indicated in the same partition....

---

### Post by Inxsible on 2007-05-30
Oh ! Snap !!
 
I didn't notice that !
 
But the surprising thing is that the GRUB still has an entry for Microsoft XP Professional !!

---

### Post by confused57 on 2007-05-30
Since you have another drive with Windows, you would probably need an entry similar to this to boot:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

See this guide for editing your menu.lst:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

