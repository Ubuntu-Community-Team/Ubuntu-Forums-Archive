---
title: "menu,lst problem"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2006-12-19
I added 2 distros, and for some reason my menu,lst doesn't work. Can anyone help me with this?  I commented out the last 2[new] entries as thats the only way I could boot.  I added what was in their menu,lst's just like I have for other distros :confused: 
.........................................................................................................
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		5

# Pretty colours
color cyan/blue white/blue
gfxmenu (hd0,10)/boot/message

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
# kopt=root=/dev/hda11 ro ramdisk_size=100000 lang=us apm=power-off nomce vga=791

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,10)

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

# Pretty colours
color cyan/blue white/blue

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout=15

## ## End Default Options ##
### BEGIN AUTOMAGIC KERNELS LIST

title		Ubuntu at hda16, kernel 2.6.15-23-386
root		(hd0,15)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda16 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu recovery mode
root		(hd0,15)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda16 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		memtest86+
root		(hd0,15)
kernel		/boot/memtest86+.bin 
boot

title		PC linuxos at hda5 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-oci6.mdk-i586-up-1GB root=/dev/hda5 ro noapic nolapic acpi=ht nomce psmouse.proto=imps splash=silent 
initrd		/boot/initrd-2.6.12-oci6.mdk-i586-up-1GB.img
savedefault
boot

title           MEPIS at hda7, kernel 2.6.15-26-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda7 nomce quiet vga=791 
savedefault
boot

title		Kubuntu at hda9, kernel 2.6.15-23-386
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda9 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Kanotix at hda11, kernel 2.6.16.16-kanotix-1
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.16.16-kanotix-1 root=/dev/hda11 ro ramdisk_size=100000 lang=us apm=power-off nomce vga=791 
initrd		/boot/initrd.img-2.6.16.16-kanotix-1
savedefault
boot

title           Freespire at hda15, Ver. 1.0.2
root            (hd0,14)
kernel          /boot/vmlinuz-2.6.14-gratis  root=/dev/ide/host0/bus0/target0/lun0/part15 rootdev=0x030f ramdisk=35392 video=vesafb:nomtrr jiffymount=noatime mem=nopentium resume2= vga=0x311 splash=silent
initrd          /boot/initrd-2.6.14-gratis.gz
savedefault
boot

#title           Berry at hdb2 kernel 2.6.18-berry
#root            (hd1,1)
#kernel          /boot/vmlinuz-2.6.18-berry
#initrd          /boot/initrd.gz
#savedefault
#boot

#title           Fedora Core at hdb3, kernel #2.6.18-1.2798.fc6xen
#root            (hd1,2)
#kernel          /boot/xen.gz-2.6.18-1.2798.fc6 
#module          /boot/vmlinuz-2.6.18-1.2798.fc6xen ro root=LABEL=/ rhgb quiet
#initrd          /boot/initrd-2.6.18-1.2798.fc6xen.img
#savedefault
#boot

### END DEBIAN AUTOMAGIC KERNELS LIST
title          Windoz 98me at hda1
root           (hd0,0)
makeactive
chainloader    +1

---

### Post by sonny on 2006-12-19
What distro's did you add?

---

### Post by macogw on 2006-12-19
Fedora and Berry...the two that are commented at the bottom.

---

### Post by mcduck on 2006-12-20
I'm not sure about that problem, but one thing you should notice is thal you should keep all other boot lines than Ubuntu's either before or after the section between lines '### BEGIN AUTOMAGIC KERNELS LIST' and '### END DEBIAN AUTOMAGIC KERNELS LIST'. Everything between these lines is automatically reconfigured during kernel updates, and that would cause you to loose all your boot options..

---

### Post by Herman on 2006-12-20
hello randiroo76073,
I agree with mcduck and also I think you should try using the 'configfile' command. That will be easier and better because it will bring up the Grub menu that belongs to each operating system so they each boot by their own menu. It means you don't need to update your menu.lst each time another operating system has a kernel update. After you try booting with the configfile command you'll probably want to change all your other OS entries too.
You need to check whether the other systems have a file called /boot/grub/menu.lst, some might have a file called 'grub.conf' or something else instead. It might be in /GRUB or some other directory. I included this example menu.lst entry to give you the idea but you might need to edit it with the correct path and filename.
```
 ### END DEBIAN AUTOMAGIC KERNELS LIST

title          Windoz 98me at hda1
root           (hd0,0)
makeactive
chainloader    +1

title           Berry at hdb2 
configfile (hd1,1)/boot/grub/menu.lst
 
 title           Fedora Core at hdb3
configfile (hd1,2)/boot/grub/menu.st

 
```Also, as mcduck said. you should move all your other entries to below the bottom of your automagic kernels list too, or they'll be automagically deleted sooner or later.

I have never heard of a menu.lst file not working due to too many entries, but if you think that could be what is happening, you can copy it with a  'sudo cp' command and rename the new copy something else. For example, call it 'menu.2nd'. Then you can put a configfile boot entry to menu.2nd at the bottom of your menu.lst. That means menu.lst will load menu.2nd for you if you select that line. You can put half of your boot entries on your menu.2nd and leave half of them on your menu.lst.
You can do lots of neat tricks with Grub if you are willing to try out ideas.
```
 title        menu.2nd
configfile  (hd0,15)/boot/grub/menu.2nd
```
Regards, Herman :D

---

### Post by randiroo76073 on 2006-12-20
Thanks McDuck & Herman, I'm off to try out your suggestions, still learning :), linux is so much easier to understand than windoz, glad I made the switch.  Even tho I bork things up it's alot easier to correct, if ya don't make mistakes ya don't learn.

---

### Post by randiroo76073 on 2006-12-20
Another question, Berry added a copy of grub to 1st partition[?] of hd1(hdb) is this something I need to configure or add to menu,lst?

---

### Post by Herman on 2006-12-20
> Another question, Berry added a copy of grub to 1st partition[?] of hd1(hdb) is this something I need to configure or add to menu,lst? Hello randiroo76073, 
If Berry installed Grub to the first sector of it's own partition (bootsector), that's okay. You can just ignore that fact or you can use it, it's up to you.

You have added a line in your Ubuntu Grub's menu to directly boot Berry's kernel, and I normally I would expect Berry would boot okay from that, so you wouldn't need to boot Berry by its bootsector unless you want to. 

Now if you tried booting Berry with a configfile command, Berry should boot up that way as well, except you don't have to specify the exact kernel that way. so it is better when it's an entry for a different Linux system, you don't have to manually update your menu.lst with the exact kernel name when Berry gets a new kernel.

When Grub is installed to an operating system's partition (first sector or bootsector), that means you also have the option of chainloading that operating system. 
You don't have to, but if you want to for an experiment, you can add an entry to Ubuntu's menu.lst with a chainloader command that will also boot Berry in a similar fashion to the way the configfile command does.
```
title          Berry
root         (hd1,1)
chainloader +1
``` That would be another way to boot Berry. (If I am guessing the partition number correctly from the menu.lst in your original post). That method is just as good as the configfile command for multiple booting other Linux distros. The only disadvantage is it takes a few more steps to install Grub to the operating system partition's bootsector, but yours is like that already, so there is no disadvantage in booting Berry that way if you want to.

Now you know the three main commands you can use with Grub for booting operating systems with. (direct kernel booting, configfile booting and chainloading). So you are learning a lot about Grub.
Grub is the best bootloader in the world and we can do all kinds of neat tricks with it. It's a lot of fun playing around with Grub and experimenting with it. You are asking very good questions. :D

Regards, Herman :D

---

### Post by randiroo76073 on 2006-12-20
Thanks for all the info Herman, it's people like you in the linux community that make it alot easier for people to make the transition :D  It's not that way in the win community, they'd rather resort to name calling & such :(  People ask why I run so many distros, because I can is answer, and it's accepted for that!  After all, linux is about choice :)

---

### Post by Herman on 2006-12-20
You are welcome, the pleasure is mine! :D
Regards, Herman

---

### Post by randiroo76073 on 2006-12-20
Some things to pass on for multiboot using "configfile" in menu,lst:
CAUTION: Always backup your main distro "menu,lst" before editing!  I have mine backed up to a folder in /home called "Backup"[original name, there]

You will probably have to edit menu,lst in other distros also.  I found that I had to delete any reference to other distros except the 1 pertaining to whatever distro I had booted into, ie: boot into Kubuntu, edit menu,lst to remove all entries for distros not Kubuntu.
Unless you like a delay comment(#) out the "Timeout" entry in "default options" section.
After these small adjustments everything is smooth sailing :D

PS: Ya, I'm a bit of a neatness freak!

---

