---
title: "Installing from External CD ROM Drive?"
date: 2007-09-24
forum: Apple PPC Users
---

### Post by OscarWabbit on 2007-09-24
hi

my computer is a G5 IMAC but the internal CDROM Superdrive is not working but i have an external firewire CD ROM Drive.

i also have an external 125GB Firewire Hard Disk.  i want to install ubuntu on this drive.

i have tried to run the feisty install CD from the external cd rom drive but it doesnt work.

is there a way i can edit any files before burning the ubuntu cd so that it will install from the external cd rom drive?

ive noticed there are 2 files in separate locations called yaboot.conf which refer to "cdrom" in the path names... i guess "cdrom" would usually point to the internal cd rom drive.  can i edit these files to get it to install from external cd rom?

which yaboot.conf file do i edit?

/install/yaboot.conf
or
/etc/yaboot.conf?

would my external cd rom drive be called something like cdrom:1 or cdrom:2 or something like that?

thanks







edit: here is a copy paste of part of the /etc/yaboot.conf file from the desktop ppc iso disk:


image=/casper/powerpc/vmlinux
	label=live-nosplash
	alias=live-nosplash-powerpc
	initrd=/casper/powerpc/initrd.gz
	append="file=/cdrom/preseed/ubuntu.seed boot=casper quiet --"
	initrd-size=1048576
	read-only


notice the file=/cdrom/pressed... bit

if i change this /cdrom/ reference globally in the file to point to the external cd rom drive, could i then burn an install cd that would run from external cd rom?

is my idea completely mad? lol

---

### Post by logos34 on 2007-09-24
Can you boot other install cds from the external cdrom?  Did you burn the ubuntu .iso as an **image**?

---

### Post by stmiller on 2007-09-24
I also had trouble trying to install Feisty with an external Firewire DVD-RW drive onto my Powerbook. In the end I had to replace the dying CDRW drive inside my Powerbook.

So this might be some kind of bug. Try the Edgy disc to see if it will boot, perhaps. Then you can always install Edgy and update to Feisty.

---

### Post by frog_pilot on 2007-09-25
Isn't it possible to hold down the alt-key during startup. There open firmware shows all bootable drives. Isn't there shown a CD-Icon with a little Penguin. I don't know, how this way would work. But I also think it can only boot from external drive, if the yaboot.conf fits with this hardware-setup.

May be it's worth a try. But not too much hope... :(

If you find out on which location your external drive is mounted, try to edit the cd's yaboot.conf. No bad idea...

The mountpoint is in /Volumes/ but the device-name... I have no idea

---

### Post by OscarWabbit on 2007-09-25
hi frog

yep, ive tried the "holding down the Alt key whilst booting" method and it does show a little penguin for the install cd in the external drive.

the thing is, when i click the icon and it goes to load the CD, the install just crashes and it then resorts back to loading mac os x from my internal hard disk.

ergo, it doesnt work, and i suspect its because the yaboot.conf file is pointing to "cdrom" device which is probably the default device of the internal cd rom drive, which on my computer is broken so i have no choice but to use the external cd rom drive.

ive looked in to the cost of replacing my internal cd rom drive and apple are charging a small fortune for it, its robbery and i refuse to pay apple the price they want for a replacement internal hard disk.








i would like to know which yaboot.conf i need to edit... is it the one in /install/ or the one in /etc/ ?

would changing the yaboot.conf file be enough or are there other files that would need changing too?

---

### Post by pxwpxw on 2007-09-26
OscarWabbit

You need to work on the /install which is the cd boot directory.

You could try booting yaboot direct, to bypass ofboot.b which is where the Apple Option menu boot fails in finding yaboot and that cant be simply specified (I dont know how).

Then yaboot.conf would also probably need a 
 device <openefirmware path to firewire cd>. 
as well as the preseed fixups, and  maybe others deeper in the install. 
To get it completely right I think it would need a re-install of the yaboot files to the loop mounted /install directory when re-mastering the iso.
Not something I would try.

If your aim is to install to the external firewire hard drive, you can do it from a standard iso in your Macosx partition on the internal drive with much better chance of success and less struggle.

Whichever way you go, there is still the fixup needed for the yaboot install to the external firewire HD.

---

