---
title: "T21 Absolute Newbie"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by timjohn on 2006-03-29
I will be installing a dual boot on my Thinkpad as soon as I receive my CD, As far as I can tell from the reading I have been doing I shouldn't have any problems, but, just in case.  Any suggestions for my particular install? What should and shouldn't work ffrom the get-go?  I've been using XP with a wireless PCMCIA card. Mostly I surf.  I'm not afraid of the command line, but it has been a FEW years so simple instruction are greatly appreciated...... Thanks, Tim:confused:

---

### Post by meborc on 2006-03-29
when searching for t21 in wiki.ubuntu.com i found this [https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadT21?](https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadT21?) 

it is quite outdated (tested on early breezy) but it could give you some idea of it... IBM is known to be a linux friend... meaning that everuthing should go OK

although, before installing you could test with live-cd to make sure everything works...

AND for dual-boot read this: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

EDIT: and a nice guide to breezy is [HERE]("http://makuchaku.info/amnesty/#")

---

### Post by erniewinner on 2006-03-29
mines a thinkpad t21. i'm running ubuntu and xandros... last night i downloaded fedora. everything seems to work good, no problems. although i don't use wireless. :cool:

---

### Post by PesVseved on 2006-06-08
I've been running breezy on T21 for 6 moths....and there are some issues worth mentioning. I could not get suspend/hibenation working. T21 doesn't seem to support apci. Therefore I switched to apm. With apm sleep works out of box........Hibernation not. After suspend there are problems with soundcard. in breezy /etc/init.d/alsa reload should fix it. However, I don't know what to do in dapper. 
There are also very good utilities for thinkpads. Just search in synaptic......
:???:

---

### Post by erniewinner on 2006-06-20
](*,) while i didn't think i had a problem with my t21 everything is cool exept the black screen and flashing cursor on bootup... it takes a few reboots to get in. i think this has been bug reported already... hope it gets fixed soon. it hasn't been done up to yet. (6.06 lts and all updates.)

---

### Post by cidica on 2006-06-20
I would seriously look into the wireless part. Everything else should fly by. Linux and wireless for me was somewhat of a pain. My wireless card used a driver that linux-wlan didnt support. So i had to make linux use a windows driver. I did by using a package called ndiswrapper. [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")
has many listing of cards that have all been testing using ndiswrapper.

---

### Post by erniewinner on 2006-07-11
:KS [http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_T21](http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_T21)

haven't tried it yet but it looks simple enough! 8) 

"1) Choose Safe Boot instead of Normal Boot. It is the second line on the boot menu.

2) Click Applications > Accessories > Terminal

3) Type: Sudo -H -s (This command gives you power to modify the xorg.conf file later.)

4) Type: gedit /etc/X11/xorg.conf (Make sure that the "X" in "X11" is capital X, and the "11" is number "eleven" not lowercase "LL".)

5) Add the following two lines into the "Device" section of your xorg.conf.

Option "BusType" "PCI"
Option "DmaMode" "None"

6) Save the file. Done! Your Thinkpad won't freeze anymore when booting into X Windows."

---

### Post by erniewinner on 2006-07-11
8) 2 reboots and doing fine! i would only offer to say that an easier way for me was: gksudo gedit /etc/X11/xorg.conf
         then add the 2 lines of text...

---

### Post by timefortea on 2006-07-20
I installed Xubuntu on my T21 because it runs somewhat slicker on the older hardware (mine's got 512Mb but Gnome just wasn't as responsive as I wanted) and I am very pleased with it, it is highly recommended.

As far as suspend/hibernate goes, I couldn't get it working with acpi - when I suspend the machine shuts down but doesn't come back; I powered it off but then I had to remove the battery to get it to switch on again. I didn't get any better results with apm. Has anyone got this working successfully?

---

### Post by djsroknrol on 2006-07-20
I edited grub with acpi=off and everything went fine on my T21 (128 ram)...a bit slow, but I know it's not a barn burner...even got my DVD working yesterday after playing with it on and off for a couple of weeks...

---

### Post by timefortea on 2006-07-20
Interesting, I couldn't get it to work, I will give it another go later. Is there anything else you did apart from acpi=off? From memory (which isn't very accurate) I remember a load of messages from the kernel about timings.

---

### Post by djsroknrol on 2006-07-20
I'm not at my Thinkpad right now, but I'll post back here in a little bit...I can't remember right off if there was anything else that I altered in Grub...

---

### Post by timefortea on 2006-07-20
Did you disable Speedstep? (and if so, how?) When I boot with acpi=off, the kernel complains that it is losing ticks and it reports the CPU speed wrongly (175MHz). Then it says:

> 
[   39.415810] Losing too many ticks!
[   39.415831] TSC cannot be used as a timesource.
[   39.415853] Possible reasons for this are:
[   39.415874]   You're running with Speedstep,
[   39.415897]   You don't have DMA enabled for your hard disk (see hdparm),
[   39.415924]   Incorrect TSC synchronization on an SMP system (see dmesg).
[   39.415948] Falling back to a sane timesource now.
[   39.415971] Losing some ticks... checking if CPU frequency changed.


finally, at the end it reports:

> 
[  185.594244] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  192.445101] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  192.445196] hdc: drive_cmd: error=0x04 { AbortedCommand }
[  192.445230] ide: failed opcode was: 0xec


When I try to suspend or sleep, the HD spins down but not up again. Then I need to poweroff and restart to get it back to life...

---

### Post by djsroknrol on 2006-07-20
Ok..here is my menu.lst from the T21:
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 acpi=off ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		***********OTHER OPERATING SYSTEMS:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

hope it helps..it works fine for me, and as you can see, it's dual booting as well...

---

### Post by timefortea on 2006-07-21
I see you are running an older kernel, I've 2.6.15-26-686 installed. Perhaps something is broken, I did see some complaints about ACPI being broken on older 2.6.15 kernels, so maybe its not quite fixed yet. Ah well, thanks for finding out for me anyway!

---

### Post by timjohn on 2006-11-06
OK, so I am ready to try again, I have tried ubuntu and xubuntu and still have a problem after a few reboots, I get to IRQ interrupts and freeze, I think this has to do with the acpi system and any help would be appreciated.  I need some really simple instructions on installing my system, once I get installed and running I can get everything else working.  Any help is appreciated and will be passed along.  Thanks, Tim

---

