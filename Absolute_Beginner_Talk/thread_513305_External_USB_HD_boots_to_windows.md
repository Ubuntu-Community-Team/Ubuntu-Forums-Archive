---
title: "External USB HD boots to windows"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-07-30
Hello,
I've perused the myriad "external hd boot" posts, but couldn't find a "noob" question like this:

How can I tell, implicitly and definitely, that my laptop (Gateway mx3701) allows external hd booting???

Here's my OS set-up.

1.  I've got Windows xp on the internal 80 NFTS HD of laptop.
2.  Have Ubuntu installed on external 80 gb USB hd ( 3 ext3 partitions -- swap, sys, and home).

When I boot from live cd, I can access all files of the external ubuntu hard drives; read, write, and execute them.  My system BIOS shows a 7 boot line-up with some (unknown) external cd-rom, ide hd, ide cd-rom, the external (ubuntu) hd, a flash drive, etc.  The sequences is external usb, then cd-rom, and finally internal IDE.

There's a lot of BIOS configs like "32-bit auto on/off, etc.) and "blocks" or something that I don't know how to configure; basically BIOS is defaults except for the boot sequence.  

When I boot (with the USB hd first in the sequence) it defaults to a windows error screen saying somethign happened with the windows OS, offers the ability to boot in "Safe Mode" with a countdown.  It seems to just bypass the USB hd.

Is my boot sequence causing problems? Do I need to do some special BIOS configs?  How can I be sure my system allows external booting?   

Here's some fdkisk -l stuff (from live cd):
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   82  Linux swap / Solaris
/dev/sda2             244        2067    14651280   83  Linux
/dev/sda3            2068       10011    63810180   83  Linux

Disk /dev/sdb: 1021 MB, 1021312512 bytes
129 heads, 16 sectors/track, 966 cylinders
Units = cylinders of 2064 * 512 = 1056768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         967      997367+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(972, 128, 16) logical=(966, 57, 15)


Finally,  I just discovered that ubuntu treats all NTFS drives as read-only (because of some formatting dilly); anyway around that without switching to FAT32?  

Thanks a ton!

---

### Post by oilchangeguy on 2007-07-30
you'll probably need to configure the bios to boot from other devices first (if that options's available).

---

### Post by johntkucz on 2007-07-30
> **oilchangeguy said:**
> you'll probably need to configure the bios to boot from other devices first (if that options's available).

okay....thanks for the response....but HOW do I do that???!  How do I know if that option's avaialbe?  Is there any online documentation I can get on my system's BIOS?  I am aware that you configure the BIOS to boot to external HD (DUH!); i'm trying to discern if 1)that's possible and 2)how to do that within the options and formatting interface of my bios.  thanks.

---

### Post by johntkucz on 2007-07-30
Anyone there?....BIOS gurus welcome....

---

### Post by oilchangeguy on 2007-07-30
> **johntkucz said:**
> okay....thanks for the response....but HOW do I do that???!  How do I know if that option's avaialbe?  Is there any online documentation I can get on my system's BIOS?  I am aware that you configure the BIOS to boot to external HD (DUH!); i'm trying to discern if 1)that's possible and 2)how to do that within the options and formatting interface of my bios.  thanks.

since you already know that you've got to configure the bios to boot from the external drive. then you should also know how to enter the bios and check (DUH!) i hate smart asses!

---

### Post by johntkucz on 2007-07-30
> **oilchangeguy said:**
> since you already know that you've got to configure the bios to boot from the external drive. then you should also know how to enter the bios and check (DUH!) i hate smart asses!

Dude, how could I be a smart *** if I'm posting questions about how to even know if my BIOS allows external booting! I'm definitely not a smart ***.  I hate people who try to provide a solution just for typing something but never give answers!  I wrote in the original message that I knew the BIOS needed to be configured, but didn't know HOW.  You're the smart *** who comes along and then tells me the BIOS needs to be configured.  Again, you're just providing unhelpful, vacuous responses (no new information).

---

### Post by oilchangeguy on 2007-07-30
now follow along. when the computer starts to boot, you should see an option to enter setup (the bios). this information is displayed only briefly, so you'll have to pay attention.

---

### Post by johntkucz on 2007-07-30
> **oilchangeguy said:**
> now follow along. when the computer starts to boot, you should see an option to enter setup (the bios). this information is displayed only briefly, so you'll have to pay attention.


now follow along?...great, we go from vacuous responses to patronizing ones.  Maybe I just  didn't convey myself clearly.  I know how to enter the BIOS menu.  I press F2 and then I'm presented with a configuration (that sort of resembles alsamixer); with a bunch of options to change boot sequence, assign primary master drive secondary slave, return to defautls (f9), saveand exit (F10).  there's about 5 different menus I can go into.  It's configuring that menu one I'm there.  Do you see how a post like "well just configure BIOS", when I'm already able to tweak (I just don't know HOW or what the hell I'm doing) some of the BIOS, sounds like you 1)never even read the first message or 2)actually like redundant useless, vacuous responses?  Okay, maybe I should have been more clear about what to do after I get into the BIOS screen.  I can access it; I just don't have any documentation on how to tweak it

Where do I look on the BIOS screen(after F2 -- already in the bios menu system)  to find if external booting is allowed? 

I haven't found  a single post that explicitly defines how to configure BIOS.

Thanks.

---

### Post by oilchangeguy on 2007-07-30
click on the tab labeled boot. from there you should see the available boot options. and be able to change them. if not, you'll need to visit the website for your motherboard, and ask them. the mobo maker is usually stamped somewhere on the motherboard.

---

### Post by johntkucz on 2007-07-30
I appreciate you trying to provide a response.  However, it seems like you've been -- after three responses -- incapable of providing new information.  This could be do to your poor habit of vacuous responses, or an inadequate description of my knowledge level.

1.  I know how to enter the BIOS menu.
2.  I have VERY LITTLE knowledge of what to do there, what things mean, etc.  

What are the indicators (it's so ridiculous how I have to spell all this out) from WITHIN bios that show whether or not you can external boot?

---

### Post by johntkucz on 2007-07-30
> **oilchangeguy said:**
> click on the tab labeled boot. from there you should see the available boot options. and be able to change them. if not, you'll need to visit the website for your motherboard, and ask them. the mobo maker is usually stamped somewhere on the motherboard.

Visit the website. I could have thought of that myself, but thanks, good suggestion.  When I go to the BOOT tab (If I remember correctly), All I see is options to change the boot sequence (via +/- keys).  

Secondly, considering that I don't really want to hack open the guts of my laptop and examine the raw motherboard, anyway to check the mobo maker externally? IT says model no: W34OUI on the bottom (and model# mx3701).  I'll check the site.

---

### Post by oilchangeguy on 2007-07-30
> **johntkucz said:**
> I appreciate you trying to provide a response.  However, it seems like you've been -- after three responses -- incapable of providing new information.  This could be do to your poor habit of vacuous responses, or an inadequate description of my knowledge level.

1.  I know how to enter the BIOS menu.
2.  I have VERY LITTLE knowledge of what to do there, what things mean, etc.  

What are the indicators (it's so ridiculous how I have to spell all this out) from WITHIN bios that show whether or not you can external boot?

i didn't think my last post was that hard to understand. do you not see a tab labeled boot, when you're in the bios? if so tab over to it and press enter. and you should be presented with the available boot options, and info on how to change them.

---

### Post by johntkucz on 2007-07-30
gateway support says says (under specs):
Chipset = ATI RC415MD

Is that the motherboard?

---

### Post by johntkucz on 2007-07-30
okay some more info

BIOS Specifications 	ACPI 2.0, WFM 2.0, SMBIOS 2.3, USB floppy disk drive boot support Phoenix Core SP2 or later
SVID and SSID: 0 × 107B and 0 × 0318


This looks like the motherboard

 - Motherboard UMA w/ATI RC415MD w/o 1394 (FRU)

---

### Post by johntkucz on 2007-07-30
> **oilchangeguy said:**
> i didn't think my last post was that hard to understand. do you not see a tab labeled boot, when you're in the bios? if so tab over to it and press enter. and you should be presented with the available boot options, and info on how to change them.

The post to which you refer did appear simple to understand.  It's just that it was too simple! I already know how to access that boot tab (under BiOS), but don't see any indication if external booting is possible (discovering that is hte purpose of this thread).

---

### Post by johntkucz on 2007-07-30
downloaded the manual for the laptop. nothing in there about tweaking bios.

---

### Post by oilchangeguy on 2007-07-30
> **johntkucz said:**
> The post to which you refer did appear simple to understand.  It's just that it was too simple! I already know how to access that boot tab (under BiOS), but don't see any indication if external booting is possible (discovering that is hte purpose of this thread).

try other devices, usb, or something to that effect. depending your your computers age these options may not be available.

---

### Post by oilchangeguy on 2007-07-30
> **johntkucz said:**
> downloaded the manual for the laptop. nothing in there about tweaking bios.

get the motherboard manual, not the computers owners manual.

---

### Post by johntkucz on 2007-07-30
> **oilchangeguy said:**
> get the motherboard manual, not the computers owners manual.


good call.  more precise.  owner's man is 95% using windows xp, basically!

---

### Post by johntkucz on 2007-07-30
> **oilchangeguy said:**
> try other devices, usb, or something to that effect. depending your your computers age these options may not be available.


Try other devices? What's that mean? Under the boot menu, I can only change the sequence of about 7 devices (usb cd-rom (? don't even have one) ide hd, ide cd-rom, usb ext hd, usb ext flash) etc.

My computer is about 1-2 years old ( I think).

---

### Post by oilchangeguy on 2007-07-30
> **johntkucz said:**
> Try other devices? What's that mean? Under the boot menu, I can only change the sequence of about 7 devices (usb cd-rom (? don't even have one) ide hd, ide cd-rom, usb ext hd, usb ext flash) etc.

My computer is about 1-2 years old ( I think).

is not usb ext hd, what you're looking for?

---

### Post by johntkucz on 2007-07-30
they only seem to have a bloody picture of the mobo! (What the hell's good will that do?)

[http://support.gateway.com/s/Mobile/Q106/Bishop/4006148R/4006148Rmv.shtml](http://support.gateway.com/s/Mobile/Q106/Bishop/4006148R/4006148Rmv.shtml)

What about

BIOS Specifications ACPI 2.0, WFM 2.0, SMBIOS 2.3, USB floppy disk drive boot support Phoenix Core SP2 or later
SVID and SSID: 0 × 107B and 0 × 0318

Does that reveal anything?

---

### Post by johntkucz on 2007-07-30
> **oilchangeguy said:**
> is not usb ext hd, what you're looking for?


Yeah it is. What I'm looking for is present under the boot menu.  (Every possible boot drive, cd-rom flash drive, etc. (And some I don't even recognize) is totally present).  Does the fact that ext usb drive is listed prove that external hd booting is possible?

If so, then what's up with my system, why does it always boot from CD or internal IDE (windows xp)?

---

### Post by oilchangeguy on 2007-07-30
> **johntkucz said:**
> Yeah it is. What I'm looking for is present under the boot menu.  (Every possible boot drive, cd-rom flash drive, etc. (And some I don't even recognize) is totally present).  Does the fact that ext usb drive is listed prove that external hd booting is possible?

If so, then what's up with my system, why does it always boot from CD or internal IDE (windows xp)?

yes it's possible. but you'll have to change the boot order, so that your external drive is first on the list.

---

### Post by johntkucz on 2007-07-30
This was very helpful (seems to be a BIOS reference of sorts):
[http://support.gateway.com/s/MOTHERBD/INTEL/SAC032AA/00000001.shtml](http://support.gateway.com/s/MOTHERBD/INTEL/SAC032AA/00000001.shtml)
It said this:
oot Options
Select this item and press ENTER to see the submenu, in which you can select several parameters that affect the computer's start-up configuration.

The Boot Device fields, First through Fourth, allow you to select the order in which your computer's hard disk, floppy disk drive, CD-ROM drive, and so forther, are booted. You select the device you want for each field by pressing ENTER to view the menu choices.

The default Boot Device order is as follows: CD-ROM, Floppy, Hard Disk, Network, and Disabled. Make sure any unused Boot Device fields are set to Disabled.

The System Cache field controls the primary and secondary cache. It is recommended to leave it set to Enabled, since setting it to Disabled degrades computer performance.

The Boot Speed field controls the computer speed. It is recommended to leave this setting to Turbo, since selecting Deturbo decreases computer performance. 

It doesn't mention "external hd" in the "default setting" but external hd's show up under the Boot options.  Can this boot from external hd?

---

### Post by johntkucz on 2007-07-30
> **oilchangeguy said:**
> yes it's possible. but you'll have to change the boot order, so that your external drive is first on the list.


I've done that; it still reverts back to the windoes internal idea (which is like 4th on the boot sequence list).

Do I have to tweak System Cache, Deturbo, Boot speed, Multiple Sector Settings or stuff like that? (of which I know little of).

---

### Post by johntkucz on 2007-07-30
Huge realizations.  When asking a problem; a question (especially a techie won) have as HIGH of an entry point as possible, otherwise people think you don't know the basics and give redundant answers.  I should mention, in this quest discover external bootability, that I already primed the boot sequence (under boot tab of BIOS menu) to have the external hd come first instead of going into all the details about my hard drive partitions!  It's best to be incredibly specific with questions to ensure more specific answers.

---

### Post by kelvin spratt on 2007-07-30
Instead of shouting down each other try working together, i don't know your mobo or your bios configuration but here are some clues what to look for you should have a entry for which h/drive to boot first, and an entry for 1st boot device, an entry for 2nd boot, you need to change 1st boot device and h/drive for external usb drive and enter your internal drive to boot 2nd, in theory if you unplug the USB drive your original drive should boot. In practice it may not work as Usb drives don't like to be first boot drive as its there nature to spin down when not in use and a lot off boxes won't boot of an external drive to linux but good luck.

---

### Post by johntkucz on 2007-07-30
I don't see anything in any help manuals about external hd booting.  There's stuff on dual-boots from partitions (of the already internal hd), but nothing on external hd boot.

---

### Post by johntkucz on 2007-07-30
> **kelvin spratt said:**
> Instead of shouting down each other try working together, i don't know your mobo or your bios configuration but here are some clues what to look for you should have a entry for which h/drive to boot first, and an entry for 1st boot device, an entry for 2nd boot, you need to change 1st boot device and h/drive for external usb drive and enter your internal drive to boot 2nd, in theory if you unplug the USB drive your original drive should boot. In practice it may not work as Usb drives don't like to be first boot drive as its there nature to spin down when not in use and a lot off boxes won't boot of an external drive to linux but good luck.

While we obviously just accidentally hit each others buttons, I think the cooperation has emerged already (although some of it went nowhere). I posted mobo and bios in previous posts:

BIOS Specifications ACPI 2.0, WFM 2.0, SMBIOS 2.3, USB floppy disk drive boot support Phoenix Core SP2 or later
SVID and SSID: 0 × 107B and 0 × 0318

Motherboard UMA w/ATI RC415MD w/o 1394 (FRU)

Okay you post helps.  Much more helpful than oilchange (no offense).  I've set the external hd as 1st boot, then cd, and then ide is about 3rd.  Because it reverts to the internal mabye the spin-down of the external usb drive could be an effect.  Anyway around that?  Thanks.

Thank you fo

---

### Post by kelvin spratt on 2007-07-30
I think  First boot device as USB drive, USB H/drive as first h/drive then internal thats how it reads on mine but as i said not many mobos support booting from external drive mine boots XP but will not boot to Linux their is some info on this forum about it somewhere

---

### Post by johntkucz on 2007-07-30
so.....this got cold.  Should I just repitively try boot sequences and hope that the external doesn't spin down?  SHould I tweak any other features like primary/secondary slave drives or system cache or something?

---

### Post by johntkucz on 2007-07-30
> **kelvin spratt said:**
> I think  First boot device as USB drive, USB H/drive as first h/drive then internal thats how it reads on mine but as i said not many mobos support booting from external drive mine boots XP but will not boot to Linux their is some info on this forum about it somewhere


I've searched the forum, but looking for mobo support. good idea.

---

### Post by kelvin spratt on 2007-07-30
i just found this it may or may not help its not the one i read but may help
[http://ubuntuforums.org/showthread.php?t=512794&highlight=usb](http://ubuntuforums.org/showthread.php?t=512794&highlight=usb)

---

### Post by johntkucz on 2007-07-30
> **kelvin spratt said:**
> i just found this it may or may not help its not the one i read but may help
[http://ubuntuforums.org/showthread.php?t=512794&highlight=usb](http://ubuntuforums.org/showthread.php?t=512794&highlight=usb)

hhhmm. yeah, thanks for the reference, but the above link references grub alot.  my boot sequence doesn't even throw grub errors (it doesnt even seem like it tries to load the hd -- wiht grub on --) yet, but there could be an answer in there, tahnks.  I'll try some boot sequences and cehck that post.  hopefully should get actiated.. thanks.

---

### Post by overownt on 2007-07-30
good luck, im trying to install ubuntu external now too :D

---

### Post by johntkucz on 2007-07-30
> **overownt said:**
> good luck, im trying to install ubuntu external now too :D

Bloody hell! Damnit! This is ridiculous.  ubuntu is smooth and sleek and fast and I love it.....but nothing WORKS!! Northing f@#$#ing works!   No sound, no external boots, not dual monitors, no routers, nothing! Damnit! 

I still haven't pinpointed if something is wrong with my BIOS.

When I try to reboot (with the exernal USB in first) it just blinks blackscreen single underscore, blinking, no errors; so I have to then reboot; and select the internal hard drive (but I can access the external hd and all files, when booting from ubuntu cd).

---

### Post by johntkucz on 2007-07-30
This is a clever and efficient OS, but half of the posts I see in beginner's are just people not being able to install a key feature and then switching back.  Ubuntu can't -- nothing can -- become mainstream with so many glitches (But, on the other hand, the actual OS is incredibly efficient and i love gnome).

---

### Post by MQMike on 2007-07-30
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

(Worked fast for daydan:
[http://ubuntuforums.org/showthread.php?t=506179](http://ubuntuforums.org/showthread.php?t=506179) )

---

### Post by johntkucz on 2007-07-31
some new funky detail.  
I COULD boot to the external hd when I installed ubuntu on the internal hd and then the external.  After trying to boot to it after installing windows xp to the internal, it didn't boot.  I think, when I installed ubuntu to the external hd, it created internal as "swap" or something.  anyways, this is ridiculous.

anyone know how to transfer over gnucash files to some windows xp program? That's the only main transfer difficulty I'll have.

---

### Post by johntkucz on 2007-07-31
> **MQMike said:**
> [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

(Worked fast for daydan:
[http://ubuntuforums.org/showthread.php?t=506179](http://ubuntuforums.org/showthread.php?t=506179) )

very informative.  never new bios= basic input output system.

---

### Post by johntkucz on 2007-07-31
Okay now, 
I'm pretty sure my system can ACCESS the external hd to boot from, but it just blinks black screen white cursor indefinitely (no grub errors).
the device ids for that external 80gb hd are 
sda1 = /home
sda2= /
sda3=swap

Whenever I boot from the internal hd (which had windows xp installed on it) it loads grub and gives this error. 
GRUB stage 1.5
Grub loading please wait....
error 22

What is up?  I can't even seem to boot from windows now.  (note upon installing to the external hd, I selected the option to "migrate" the windows account, and that just seemed to create a few empty folders)

---

### Post by johntkucz on 2007-07-31
my menu.lst file (while booting from livecd) in /media/disk/boot/grub is :

```
ubuntu@ubuntu:/media/disk/boot/grub$ cat menu.lst
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

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=3a79ad82-eb61-4d85-a3b3-08b8e5396b4a ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=3a79ad82-eb61-4d85-a3b3-08b8e5396b4a ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

ubuntu@ubuntu:/media/disk/boot/grub$ 

```

---

### Post by johntkucz on 2007-07-31
i've begun tweaking the menu.lst file, but everyone says you can "change the timeout to 10 seconds or 3 seconds" I understand that is the timeout to select a boot option before the default loads,...but how do you select a boot option?

---

### Post by MQMike on 2007-07-31
--  Sounds like you may have to re-install grub (as explained in that USB reference or the How-To below).

How is BIOS (and therefore GRUB) seeing your external USB HD?  as hdz for what value of z?
Your Windows drive is seen as (hd0, 0), right?

If you get a GRUB prompt (by typing sudo grub), two things you can do to find out some info on your drives:

find  /boot/grub/stage1
That returns some (hdx, y).  That’s the value you want to put in your root (hdx, y) command.

Or, at a grub prompt, geometry (hd0) and geometry (hd1) will tell you about your drives and you can identify what OS is where.

Also, on installing grub (using root (hdx, y) – setup (hdz) – quit):
I’ve got this How-To:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(See the second post, too.)


--  That black screen, I don’t know if you have to configure Ubuntu for your monitor/video card.
That’s the business of the command:   sudo dpkg-reconfigure xserver-xorg   

xserver-org  How to get started with no GUI, Blank Screen in Linux, first time
[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)
How to start the CLI and do like:  sudo dpkg-reconfigure xserver-xorg
(dibl @ Kubuntu - may have to modify for Ubunbtu commands etc.)

After running sudo dpkg-reconfigure xserver-xorg  , you then run:  startx

More complete how-to:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by johntkucz on 2007-07-31
thanks mike, i'll check out those how-tos and repost probably. hopefully they'll take me some place with a dualboot!  Also, all the how-tos recommend changing /boot/grub/menu.lst, which is what I did, but they don't specify on which drive (mainly because it coudl be obvious).  But I've been changing the /boot/grub/menu.lst file on the external hd, 2nd partition.

also, what is " (hdx, y)."

what does that stand for? x, y?

---

### Post by johntkucz on 2007-07-31
```

How is BIOS (and therefore GRUB) seeing your external USB HD? as hdz for what value of z?
Your Windows drive is seen as (hd0, 0), right?
```

how am I going to solve this if people keep asking me questions to my questions about questions?!! Bloody hell!!!

know idea to what you're referring.  in my bios boot sequence there's about 7 different options ide hd, ide cdrom, usb f(something), usb traveldrive, usb cdroom (of which I don't have one); not sure what the external one is, but it's strange that when I boot from internal (xp) i get grub error but boot from external ubuntu get the blinking cursor on black screen (i waited that out almost an hour. nada).

---

### Post by johntkucz on 2007-07-31
grub methods how-to especially helpful.

here's 
fstab.

Note: I am checking this under the /media folder of the external hd.  there is know /boot/grub folder when you boot from live cid.  

ubuntu@ubuntu:/media/sdd2_root/boot/grub$ cat /media/sdd2_root/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3a79ad82-eb61-4d85-a3b3-08b8e5396b4a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=eeb84bb0-7e4e-463a-8ad3-916bf67774c1 /home           ext3    defaults        0       2
# /dev/hda1
UUID=9858328CE07FB76E /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=087fa5ff-dd64-478e-9343-257b9765c2f8 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
ubuntu@ubuntu:/media/sdd2_root/boot/grub$

---

### Post by johntkucz on 2007-07-31
figured out the syntax.
hdx,y --> x=HD and y=partition.

but what is going on. am I editting the correct menu.lst file?

---

### Post by johntkucz on 2007-07-31
fdisk -lu doesn't even recognize my internal xp hd I don't think

```
ubuntu@ubuntu:/media/sdd2_root/boot/grub$ fdisk -lu

Disk /dev/sda: 2063 MB, 2063597568 bytes
255 heads, 63 sectors/track, 250 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     3727079     1863508+  83  Linux
/dev/sda2         3727080     4016249      144585    5  Extended
/dev/sda5         3727143     4016249      144553+  82  Linux swap / Solaris

Disk /dev/sdc: 1021 MB, 1021312512 bytes
129 heads, 16 sectors/track, 966 cylinders, total 1994751 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          16     1994750      997367+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(972, 128, 16) logical=(966, 57, 15)

Disk /dev/sdd: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   127620359    63810148+  83  Linux
/dev/sdd2       127620360   156922919    14651280   83  Linux
/dev/sdd3       156922920   160826714     1951897+  82  Linux swap / Solaris
ubuntu@ubuntu:/media/sdd2_root/boot/grub$ 


```

---

### Post by johntkucz on 2007-07-31
> **MQMike said:**
> --  Sounds like you may have to re-install grub (as explained in that USB reference or the How-To below).

How is BIOS (and therefore GRUB) seeing your external USB HD?  as hdz for what value of z?
Your Windows drive is seen as (hd0, 0), right?

If you get a GRUB prompt (by typing sudo grub), two things you can do to find out some info on your drives:

find  /boot/grub/stage1
That returns some (hdx, y).  That’s the value you want to put in your root (hdx, y) command.

Or, at a grub prompt, geometry (hd0) and geometry (hd1) will tell you about your drives and you can identify what OS is where.

Also, on installing grub (using root (hdx, y) – setup (hdz) – quit):
I’ve got this How-To:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(See the second post, too.)


--  That black screen, I don’t know if you have to configure Ubuntu for your monitor/video card.
That’s the business of the command:   sudo dpkg-reconfigure xserver-xorg   

xserver-org  How to get started with no GUI, Blank Screen in Linux, first time
[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)
How to start the CLI and do like:  sudo dpkg-reconfigure xserver-xorg
(dibl @ Kubuntu - may have to modify for Ubunbtu commands etc.)

After running sudo dpkg-reconfigure xserver-xorg  , you then run:  startx

More complete how-to:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

blackscreen with blinking white cursor has nothing to do with video card!!! How could it? everything boots fine in other formats.  I've successful installed ubuntu on internal hd, but can't on the external.

---

### Post by johntkucz on 2007-07-31
here's the main problem.

I've tweaked the menu.lst file that's on the external ubuntu hd, but when i disconnect that drive and try to boot from internal xp windows, it can't even do that -- and tries to load grub.  How does the internal ide config even "know" about grub if the external hd is disconnected? what was changed?

---

### Post by johntkucz on 2007-07-31
I've never even seen the grub menu shown in

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

how do I access that in the startup sequence?

---

### Post by johntkucz on 2007-07-31
thread continued here:
[http://ubuntuforums.org/showthread.php?p=3112814#post3112814](http://ubuntuforums.org/showthread.php?p=3112814#post3112814)

---

