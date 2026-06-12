---
title: "How to install Feisty Fawn 7.04 on Pismo via Firewire?"
date: 2007-05-03
forum: Apple PPC Users
---

### Post by muffpuff on 2007-05-03
This is the equipments I've got and my journey with Ubuntu so far:

Pismo G3 laptop with 512 RAM running at 400 mhz
The built in DVD-ROM drive does not work anymore, So
I've built myself an External Firewire DVD reader / CDRW writer instead because I've got this 5.25 inch external enclosure lying about.
MAC OS X can be installed with no problem, using the option key when booting up
but I want Ubuntu!  

I've tried Ubuntu Feisty Fawn 7.04 PPC and the alternative ISO already but it just refuses to boot.

When I hold the option key during boot, I can see the ubuntu with firewire icon and when I press it it does go to the next screen which is similar to the first screen but blurrier, so I press it again.  Then it just dumps me into the bios.  Leaving me with no choice but to reboot or shut down.

I've gone through the forum briefly and read somewhere I need to recompile the install disc, that sounds totally drastic.  Can I do this under the windows enviroment?  Where are the instructions?

btw, I've installed Xubuntu 6.10 before the built in DVD ROM drive gave up and thought ubuntu kicked ****!

Just one more newbie question though, can ubuntu be used with just one mouse button?

over to you guys now...

---

### Post by jackoverfull on 2007-05-04
i think that the problem is that yaboot searches the kernel (or the root image) on the vrong device (the cd: openfirmware device).

i don't have the disk with me today, so i can't help you now, but in the future i think that i can do something… maybe. ;-)

2 questions:

booting the from cd you see the yaboot welcome, then when you try to boot a kernel (for example pressing "return") it boot then fails (maybe with the "can't find root partition" error) or it doesn't boot at all (something similar "can't find Linux-ppc")?

the question #2 will seem a little strange, but i need this information simply because every mac model is different regarding open firmware (what you called "the bios").
insert your mac os x installation dvd/cd, open Sistem Preferences, go in the Startup Disk pane and select it, then close System Preferences.
now open the Terminal (/Applications/Utilities/Terminal) and insert

```
nvram -p | grep boot
```
then press "return".
it will print some settings, i need to know what "boot-device" is.

---

### Post by muffpuff on 2007-05-10
Dear Jackoverfull,

Took me a few days to install tiger back on the pismo powerbook.  Here are the answers that will hopefully crack Feisty Fawn into my Carrie Bradshaw laptop :) 

When I try to boot the Ubuntu CD via Firewire, I can see the ubuntu icon, I click on it once, nothing happens, I click on it again, dumps me into the open bios with the options of boot from CD or shut down.  I need to type those commands to make the powerbook boot from internal DVD ROM drive or shut down.  No option for booting from firewire.

Going through your 2nd question produced this output:

boot-device       mac-io/ata-4@1f000/@0:3,\\:tbxi

Over to you, ninja.

---

### Post by jackoverfull on 2007-05-11
good: it doesnt seem too bad!

and you will not need to modify the cd itself, only to mess a little with the bootloader…

i just tried on my ibook with a lacie external firewire drive, wich has the same problem (like any other external drive: it is not a problem of the drive, it is the way the bootloader was configured that works only with the internal cd…) an d succeded to boot.
i only have a dapper drake cd, so i can't send directly the file (it will be different…), but i can tell you how to make it work…

1) copy the bootloader and its configuration file to the root of your mac os x partition. the bootloader is called "yaboot", it's configuration file "yaboot.conf", they're locatedc (on my cd) in the "install" folder. simply copy these 2 files at the top level of your os x partition.

2) open (textedit will be fine) the yaboot.conf file you just copied

3) at the top of the file add
```
device=mac-io/ata-4@1f000/@0:
partition=2
```

now the file should look like

```
device=mac-io/ata-4@1f000/@0:
partition=2
## This yaboot.conf is for CD booting only, do not use as reference.
## Ubuntu PowerPC (dapper)
[etc...]

```
save it and quit.

4) reboot yur mac and press command-option-o-f (the "command" key is the one with the Apple logo, the "option" one has "alt" printed on it), you will be dropped in the open firmware shell (a blank screen with some greetings in black text).

5) write

```
boot hd:\yaboot
```
and press return, usually it is enough, if not you will probably need to specify the partition too (i'll tell you how…)

good luck! :guitar:

---

### Post by jwbaker on 2007-05-11
Hi, I'm a fellow Pismobuntu user.  If I were you, I'd just netboot the installer, assuming you have a second computer.

---

### Post by didg on 2007-05-11
Does feisty netboot? IIRC initrd image is too big (> 6MB)

---

