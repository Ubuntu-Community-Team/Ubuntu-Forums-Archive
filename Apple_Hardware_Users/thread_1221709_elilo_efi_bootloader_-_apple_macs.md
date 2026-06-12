---
title: "elilo efi bootloader - apple macs"
date: 2009-07-24
forum: Apple Hardware Users
---

### Post by pxwpxw on 2009-07-24
This thread is for elilo.efi booting Apple Intel Macs.
(elilo is also used for other efi/linux systems).

elilo.efi from ubuntu package elilo 3.8-1ubuntu1 is booting ubuntu910 on IMAC81, MBP41, and MBP5x, kernel version 2.6.30-8/9ubuntu. 

elilo.efi is an alternative to grub.efi for bootloader.

It is small and fast but needs a bit more work to expand its scope for Apple intel.
```

apt-get install elilo

```

(this also installs efibootmgr).
efibootmgr uses efivars, but efivars module may be missing. This is just a configuration tool and absence does not prevent the elilo installer from installing elilo.efi.

By default the elilo installer installs elilo.efi vmlinuz initrd.img and elilo.conf to the Apple EFI 200MB fat32 partition, where it is seen by rEFIt because it is in the /efi/xxx/ directory.

elilo.efi can installed on and booted from external drives.

With kernel copies installed alongside elilo.efi, the linux root file system can be anywhere the kernel can see ( this is the same for other bootloaders ), however elilo.efi has limitations to what partitions it can see.

elilo.efi from ubuntu package elilo 3.8-1ubuntu1 is booting ubuntu910 on IMAC81, MBP41, and MBP5x, depending on kernel version. MBP5x need an efi boot to enable choice between dual graphics hardware.

In a simple configuration, elilo.efi gives a fast default boot, under 20 seconds to desktop for ubuntu910 on a Imac81 or MBP41, both using fbdev xorg driver. With the MBP5x the nvidia fdriver can be used (any confrmation anyone?) as suggested int the MBP5-2 wiki. .
 
elilo supports Graphic Output Protocol (Gop) which is used on MBP5x. (see About rEFIt info from rEFIt screen). It  also provides a simple text chooser boot menu for UgaDraw graphics on earlier macs (MBP4x Imac8x). At present this prevents any boot messages display when booting from the Option start Apple boot screen (icons), so is only usable set for default boot on UgaDraw macs, and display freezes until it the  kernel loads.

This version only runs later kernel version 2.6.30-8-generic (ubuntu). Not suuccessful 2.6.26---28, or 2.6.31

For hackers, the elilo source package compiles with the gnu-efi libraries. The unpacked source is under 1MB compared with 14MB for grub2 (which is much more versatile).
```

apt-get gnu-efi
apt-get build-dep elilo
apt-get source elilo

```

 Latest version from sourceforge. 
[http://sourceforge.net/projects/elilo/files/](http://sourceforge.net/projects/elilo/files/)

---

### Post by pxwpxw on 2009-07-24
Some more information about configuration details for elilo.efi locations and elilo.conf -

By default the elilo package installer installs elilo.efi vmlinuz initrd.img and elilo.conf to the Apple EFI 200MB fat32 partition, where it is seen by rEFIt because it is in the /efi/xxx/ directory.

A manual installation can be used to copy vmlinuz initrd.img and  elilo.efi to a hfsplus partition (possibly MacOSX partition), there are no extra modules. 

Contrary to some old documentation elilo.efi can also be installed on an hfsplus partition and blessed,
i.e. anywhere grub.efi can be installed and run.

The elilo.conf menu can be written to load kernels from other partitions (e.g. d003:/vmlinuz ---- ), but elilo.efi has limitations in what it can see. At present - only the first 4, not ext4, not some external partitons, ...), also the sequence of allocation is far from intuitive or consistent over different hardware. 

(If you set delay=0 you won't see any boot menu).

From the elilo.efi boot menu (simple text chooser),

TAB lists images.

From the elilo boot: prompt
```

boot:
? is help
 =  lists elilo device names and EFI names 
 &  list the default path
 %  list variables

<imagename> <TAB> lists the commandline.

```

( elilo.conf and other info to be added .. )

---

### Post by Nikos.Alexandris on 2009-07-30
I have ext4. This means that I should just forget testing it, right?

---

### Post by pxwpxw on 2009-07-30
> **Nikos.Alexandris said:**
> I have ext4. This means that I should just forget testing it, right?

No not a problem with the kernel copied to elilo partition (as in the standard  install), the kernel can then find ext4 ok.
It just prevents elilo from loading kernel from ext4.
I am booting karmic on ext4 here with elilo (Imac81 or MBP41).

But I can only get elilo to boot karmic 2.6.30 kernel, however some of the other MBP5x issues might be better with 2.6.30 and I boot with elilo amd no special commandline options.

Been looking at this for grub.efi, elilo and grub-pc.

Different results for dmidecode, dont know if it is significant.

karmic without noefi, or jaunty with grub-pc boot.

pxw@im:~$ sudo dmidecode | head
# dmidecode 2.9
# SMBIOS entry point at 0xbfec5000
SMBIOS 2.4 present.
44 structures occupying 1952 bytes.
Table at 0xBFEC4000.

Handle 0x0000, DMI type 4, 35 bytes
Processor Information
	Socket Designation: U2E1
	Type: Central Processor
==================
karmic or jaunty with noefi option.

pxw@im:~$ sudo dmidecode | head
# dmidecode 2.9
Legacy DMI 2.4 present.
44 structures occupying 1952 bytes.
Table at 0xBFEC4000.

Handle 0x0000, DMI type 4, 35 bytes
Processor Information
	Socket Designation: U2E1
	Type: Central Processor

===================

---

### Post by Nikos.Alexandris on 2009-07-30
> **pxwpxw said:**
> No not a problem with the kernel copied to elilo partition (as in the standard  install), the kernel can then find ext4 ok.
It just prevents elilo from loading kernel from ext4.
I am booting karmic on ext4 here with elilo (Imac81 or MBP41).

But I can only get elilo to boot karmic 2.6.30 kernel, however some of the other MBP5x issues might be better with 2.6.30 and I boot with elilo amd no special commandline options.

...

===================

OK, I'll have to wait a bit then for 2.6.30 :-(

---

### Post by pxwpxw on 2009-08-08
at 20090808
elilo is not booting karmic alpha3 2.6.31 kernel, something cahnged in kernel?

bug report -
[https://bugs.launchpad.net/bugs/408378](https://bugs.launchpad.net/bugs/408378)

It is booting ubuntu 2.6.30 kernel from karmic alpha2
and 2.6.29.4-167.fc11.x86_64 from fedora-11.
so it may boot debian 2.6.29 kernel.

---

