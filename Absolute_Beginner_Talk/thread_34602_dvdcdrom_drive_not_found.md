---
title: "dvd/cdrom drive not found"
date: 2005-05-15
forum: Absolute Beginner Talk
---

### Post by garnertr on 2005-05-15
Greetings,

I've been playing around w/ unbuntu for about a week, love what I see; However, I have an issue w/ my laptop's DVD/CDROM drive, its just not being "seen" by Ubuntu and I'm a dweeb @ Linux so pls forgive.

I have installed all of the movie players, codecs, whatnots and everything is the same it just doesn't see my drive.

One person suggested to look in my devices for the device name, which is:

hda

/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0


I believe something is supposed to be there, to point to my drive, but I don't see it.

I have a Alienware, Area 51 Sentia, 1700-Mhz, Pentium IV system.  My drive is listed in the Device Manager, and shows up as correctly in the boot-up when I hit F8.  The driv is SM-MATSHITA DVD-RAM UJ-811  it is a DVD/R-RW and CDR-RW.

This is the ONLY thing holding me back... so any tips, pls point the way; thanks!!!

---

### Post by monchichi on 2005-05-15
/dev/hda points to your hard drive.
CD/DVD drives are generally /dev/hdc or /dev/hdd.

Try running the following in a terminal:```
ls /dev/hd*;ls/dev/sd*
``` if it returns anything other than hda*, then put a disc in the drive and run the following (replacing hdc with hdd or whatever if necessary):```
sudo mkdir /media/cdrom
sudo mount -t iso9660 /dev/hdc /media/cdrom
``` and the disc should mount in /media/cdrom. You would then want to add an appropriate line to your /etc/fstab file, if you need help doing that feel free to ask here.

---

### Post by garnertr on 2005-05-15
Thank you for the reply this DVD/CD ROM issue is the only thing that is keeping me from being a 100% full time user in Ubuntu.  Anyway; THANK YOU for the reponse, this is my terminal response from what you suggested I type:

root@laptop:/home/tom # ls /dev/hd*;ls/dev/sd*
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda5
bash: ls/dev/sd*: No such file or directory
root@laptop:/home/tom #

---

### Post by monchichi on 2005-05-15
That is very weird, it seems that your kernel isn't loading the cd-rom modules.

run:```
sudo modprobe cdrom
``` then see if your drive comes up as /dev/hdc or /dev/hdd. if that works, then add the following to the /etc/modules file:```
ide-cd
sr-mod
cdrom
```and restart your computer.

---

### Post by monchichi on 2005-05-15
Oh and, you may want to edit your hostname out of your response, as it is your IP address, and you're in the newbie forum! Dangerous...

---

### Post by garnertr on 2005-05-16
[QUOTE=monchichi]That is very weird, it seems that your kernel isn't loading the cd-rom modules.

run:```
sudo modprobe cdrom
``` 

When I type that code in and I hit enter, it goes to the next line only.  nothing happens, no response.

Thanks about the IP address, I'll change that one right away!

---

### Post by Stormy Eyes on 2005-05-16
[QUOTE=garnertr]When I type that code in and I hit enter, it goes to the next line only.  nothing happens, no response.[/QUOTE]

Modprobe doesn't give any response unless it encounters errors. Try doing "sudo ls /dev/hd*" again along with the suggested operations for mounting and editing /etc/fstab.

---

### Post by garnertr on 2005-05-16
[QUOTE=monchichi]/dev/hda points to your hard drive.
CD/DVD drives are generally /dev/hdc or /dev/hdd.

roger that on the drives, makes sense for c and d not a!

Try running the following in a terminal:```
ls /dev/hd*;ls/dev/sd*
``` if it returns anything other than hda*, then put a disc in the drive and run the following (replacing hdc with hdd or whatever if necessary):```
sudo mkdir /media/cdrom
sudo mount -t iso9660 /dev/hdc /media/cdrom
``` and the disc should mount in /media/cdrom. You would then want to add an appropriate line to your /etc/fstab file, if you need help doing that feel free to ask here.[/QUOTE]


when I type that in:

root@Laptop:/home/tom #
root@Laptop:/home/tom # sudo mkdir /media/cdrom
mkdir: cannot create directory `/media/cdrom': File exists
root@Laptop:/home/tom # sudo mount -t iso9660 /dev/hdc /media/cdrom
mount: special device /dev/hdc does not exist
root@Laptop:/home/tom #

---

### Post by Stormy Eyes on 2005-05-16
What are your current results for **ls /dev/hd*** after doing **modprobe cdrom**? It could be that your CD-ROM is /dev/hdb.

---

### Post by garnertr on 2005-05-16
[QUOTE=Stormy Eyes]Modprobe doesn't give any response unless it encounters errors. Try doing "sudo ls /dev/hd*" again along with the suggested operations for mounting and editing /etc/fstab.[/QUOTE]

Ahhh errors, ok, I see, thank you for that one... the response is:

root@Laptop:/home/tom # sudo ls /dev/hd*
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda5
root@Laptop:/home/tom #

---

### Post by garnertr on 2005-05-16
[QUOTE=Stormy Eyes]What are your current results for **ls /dev/hd*** after doing **modprobe cdrom**? It could be that your CD-ROM is /dev/hdb.[/QUOTE]

After modprobe cdrom:

root@Laptop:/home/tom # ls /dev/hd*
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda5
root@Laptop:/home/tom #

the 2nd line is all yell w/ black background.

---

### Post by monchichi on 2005-05-18
Okay, this might involve loading a driver for your ide chipset or something?
(This might be getting a little out of my league)
 
What kernel are you using, and what is your motherboard's ide chipset?

If you don't know, the following will tell you:```
uname -r 
cat /proc/pci | grep -i ide
```Also, try each of the following to see any system messages relating to your ide bus:```
dmesg | grep -i ide
cat /var/log/messages | grep -i ide
cat /var/log/syslog | grep -i ide
```

---

### Post by garnertr on 2005-05-18
0) Okay, this might involve loading a driver for your ide chipset or something?

What kernel are you using, and what is your motherboard's ide chipset?

1) uname -r

2.6.10-5-386



2) cat /proc/pci | grep -i ide

root@Andromeda:/home/tom # cat /proc/pci | grep -i ide
cat: /proc/pci: No such file or directory



3) bus:dmesg | grep -i ide

root@Andromeda:/home/tom # dmesg | grep -i ide
BIOS-provided physical RAM map:
CPU: After generic identify, caps: a7e9fbbf 00000000 00000000 00000000 00000180 00000000
CPU: After vendor identify, caps: a7e9fbbf 00000000 00000000 00000000 00000180 00000000
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH4: IDE controller at PCI slot 0000:00:1f.1
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
Probing IDE interface ide0...
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
root@Andromeda:/home/tom #

---

### Post by garnertr on 2005-05-18
4) cat /var/log/messages | grep -i ide

root@Andromeda:/home/tom # dmesg | grep -i ide
BIOS-provided physical RAM map:
CPU: After generic identify, caps: a7e9fbbf 00000000 00000000 00000000 00000180 00000000
CPU: After vendor identify, caps: a7e9fbbf 00000000 00000000 00000000 00000180 00000000
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH4: IDE controller at PCI slot 0000:00:1f.1
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
Probing IDE interface ide0...
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)

---

### Post by garnertr on 2005-05-18
Question, I noticed that it stated I have 2.6.1-5-386 installed.

I have a Pentium 4, shouldn't I be using -686 flavor?  would this possibly create an issue?

---

### Post by monchichi on 2005-05-19
The 386 kernel should run perfectly on a 686 machine. You may want to install the 868 kernel to get the most out of your processor, however. Do a ```
sudo apt-get install linux-image-686
``` and if you need Nvidia driver do a ```
linux-restricted-modules-686
``` as well.

And your drive situation:

gah, do a ```
sudo lspci | grep -i ide
``` to find out what your ide controller is. I can't be of much other help, trying tweaking your BIOS settings, make sure that PnP OS is turned off. It's weird, the kernel recognizes the ide1 controller and then when it probes the device nothing returns.

---

### Post by garnertr on 2005-05-19
root@Andromeda:/home/tom # sudo lspci | grep -i ide
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
root@Andromeda:/home/tom #

---

### Post by garnertr on 2005-05-19
Question if you upgrade to 686 can you downgrade to 386 the same way?

Reason i'm asking is after apt-get 686 modules, rebooted, my laptop is now taking FOREVER to boot-up, under the 386 modules it would take about 30-35 seconds to go through everything, now...its taking just under 10-minutes and its sitting on the Loading Modules portion...yawn...

So if I can apt-get install 686 whatever, can I do the reverse?  apt-get install 386?  Looks like something in the 686 doesn't like my laptop...

---

### Post by garnertr on 2005-05-19
some other stats for you:

Primary IDE - MASTER - HD
Primary IDE SLAVE - n/a

SECONDARY IDE MASTER - ATAPI CDROM
SECONDARY IDE SLAVE - n/a

DEV ATAPI CDROM
VENDER MATSHITADVDRAM UJ-811
LBA MODE - SUPPORTED
PIO MODE 4
ASYNC DMA - MULTIWORD DMA2
ULTRA DMA - ULTRA DMA-2

AMI BIOS VER 08.00.09
BUILD 10/16/03
ID 24II109

----

Not sure if any of that is important, but I thought I'd post it...

---

### Post by garnertr on 2005-05-29
Something odd this morning happened.  Yesterday, I slicked my laptop; re-installed via my external dvd multi-recorder by LG (USB port) kepted the i386 flavor, updated all security patches and then I placed my Ubuntu burn in to my laptop's dvd player, killed the system; went to bed.

This morning, I rebooted the laptop for giggles, I was adding a tasker note to Evolution and I noticed that on my desktop my unbuntu disc icon was listed.  Now this is VERY odd I said to myself and not remembering last night, I thought that I left my LG drive on.  For giggles I right-clicked/ejected and BLAM my dvd on the laptop opened.

So, I grabbed a music cd (commercial, bought/paid for) and placed it into the drive and would you know?  IT STARTED TO WORK!!!

I quickly grabbed my Walking Tall DVD and placed it into my drive and GUESS WHAT?  IT RECOGNIZES IT, I doesn't play, but hell, I'll accept the icon on my desktop and TOTEM trying to "play" it... so I'm 1000000 times closer than I was before.

I DON'T KNOW what happened and I cannot tell you WHY its working, but for now Ubuntu seems to be seeing my hardware, I don't know why, but it is!!!

THANK YOU ALL for your support and effort these past few weeks and if I can provide anything that my help justify why its working, pls state so and I'll do my best to get it updated and posted.

Right now the only error is fr TOTEM and it says "Totem could not play 'dvd://'.  Could not read from resource.

Not sure about that, but for now, I'm happy, just to get closer to my dream.

I'm still sticking w/ Ubuntu and I am one happy camper - for right now!!! yeah!!!

----

Could it be some patch came out?  maybe slicking the drive again?  Really odd... \\:D/

---

### Post by minstrel on 2006-11-09
My device name appears as /dev/cdrom. 

Try mounting that using the instructions given before.
It is an IDE cdrom installed on a Dell2450.  
Using Ubuntu Server 6.06

---

