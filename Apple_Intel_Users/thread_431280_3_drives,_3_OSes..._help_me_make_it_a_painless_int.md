---
title: "3 drives, 3 OSes... help me make it a painless intstall?"
date: 2007-05-02
forum: Apple Intel Users
---

### Post by majoridiot on 2007-05-02
this isn't the usual triple-boot situation that seems to be covered everywhere...

i'd like to triple boot feisty, osX and XP from three different drives... since trying 
to do it with osX on one drive and XP/feisty on another seems to have hosed my osX install.

i'm totally new to macs, so i need a little help.  my intent:

hda osX
hda XP
sda feisty

and one bootloader (pref. grub, since it's what i'm familiar with) to load all 3 from a menu.

i'd appreciate help with a sane install procedure to keep me from pulling out hair along the way. :lolflag:

---

### Post by ronocdh on 2007-05-02
Please give us more information about your hardware, so we understand the environment for whatever setup is necessary. Benanzo IIRC has been trying to get Ubuntu to boot from an external drive, and even then I think he uses rEFIt. I await correction on that.

---

### Post by majoridiot on 2007-05-02
nothing complicated needed- each OS only needs boot from its own drive and run from there- i.e. no need to
share data between drives, network shares, etc.

operations and hardware-wise, they all work fine individually. i'm just trying to find a boot solution with the appropriate 
install order, etc. to keep me from death-by-constant-install-boredom.

btw- feisty, XP SP2 and osX 10.8.4

---

### Post by majoridiot on 2007-05-04
ok... the dearth of suggestions led me to slog through this the hard way... but i did get it going.

for anyone who might stumble on this later, this is what i did:

i had a working osx installation on IDE1, so i disconnected the IDE cable and hooked it up to IDE2
installed XP on IDE2, shutdown and disconnected the IDE cable
connected the SATA cable and installed feisty

shut down and connected IDE1 as master IDE2 as slave, left SATA as-is

booted and went into bios setup
configured drive order to SATA, IDE1, IDE2- boot from SATA

rebooted into feisty and checked to ensure the drives were as i intended with:

```
$ sudo fdisk -lu
```

it showed the disks as i had intended with osx on /dev/hda, xp on /dev/hdb and feisty on /dev/sda...

next, i read a lot about grub.  then, i configured the grub drive mapping:
```
$ sudo nano /boot/grub/device.map
```

when i began, it showed:
```
(hd0)  /dev/sda
```

i changed it to read:
```
(hd0)  /dev/sda
(hd1)  /dev/hda
(hd2)  /dev/hdb
```

then i added them to the menu:

```
$ sudo nano /boot/grub/menu.lst
```

i commented out the "hiddenmenu" option to show the menu and commented out "timeout" to disable the 
default boot.  then i added the menus themselves, at the tail of the file, after ### END DEBIAN AUTOMAGIC KERNELS LIST:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

title		OsX
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title		XP
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

the "root" entry points to the device mapping per device.map
savedefault to save the default boot entry (i added this in case i enable a default boot preference)
makeactive to make it an active partition

then, because each os needs to boot from the first device... i needed to swap out that drive with the
currently defined hd0 (the SATA drive).

first map the SATA to the drive to be swapped in
second map to make the intended IDE the new hd0
chainloader +1 to boot it

---

### Post by ronocdh on 2007-05-04
Congratulations on the successful setup! It's a great post to have in the forums here; hopefully someone will find it quite useful.

Your situation was, for me at least, quite difficult to understand because I had no idea what kind of hardware you were using to do this. Mac Pro? MacBook? USB externals, FireWire, IDE? Etc.

Just so you don't think we were ignoring you. ;)

---

### Post by majoridiot on 2007-05-04
> **ronocdh said:**
> Congratulations on the successful setup! It's a great post to have in the forums here; hopefully someone will find it quite useful.

Your situation was, for me at least, quite difficult to understand because I had no idea what kind of hardware you were using to do this. Mac Pro? MacBook? USB externals, FireWire, IDE? Etc.

Just so you don't think we were ignoring you. ;)

i just read my posts and yes... i was slightly less than specific.  i could blame that on any number of factors, but 
obviously i earn my nickname along the way.

i never thought i was being ignored, so no worries.  :D

---

### Post by benanzo on 2007-05-04
This confirms one big thing for me: OS X can be booted from a legacy bootloader on the MBR.

I have been doing some research on how to do a single Ubuntu install on a MacBook using ONLY the EFI/GPT and without any BIOS emulation / MBR voodoo.

I am trying to gain some understanding of how ELILO/GRUB2 will handle this.

So far I have learned that on every GPT disk (what macintels are) there is a protected MBR portion as the first block.  This prevents "dumb" partitioners from misreading the disk table and overwriting the GPT partitions.  rEFIt merely makes sure that this MBR is perfectly syncronized with the rest of the GPT so that even if a "dumb" partitioner or bootloader doesn't know anything about the GPT it still knows enough not to mess anything up.

ELILO has been booting ia64 kernels for awhile now.  The reason is because the ia64 kernels possess the necessary components to interact with the EFI.  A complicated handoff has to happen from the moment the EFI hands control to the bootloader and then to the kernel.  The kernel has to properly accept control or it will panic.  The current generic kernel (which I have installed on my macbook) doesn't contain the necessary code to interact with the EFI.  This was apparent when I apt-get installed elilo which installed efibootmgr.  In order to use efibootmgr to manipulate the built-in EFI boot parameters your kernel has to be using the module efivars.  efivars is nowhere to be found in my generic kernel.  So neither ELILO or efibootmgr is any use to me (i think).

So, until the generic kernel gets native EFI support (efivars is compiled in among other things) we can't utilize ELILO (or even GRUB2 i think) to do a native EFI boot.  We'll have to continue using GRUB/LILO to boot from the MBR.  rEFIt at least gives us a nice boot menu.  There's been talk on the GRUB2 mailing list about some limited animation functionality coming with the GRUB2 boot menu.  This could supersede the great OS X booting experience.  That coupled with Ubuntu's goal of having a slick boot (no console output whatsoever during boot) could really be a great thing.

Your input welcome!

---

