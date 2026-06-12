---
title: "Ubuntu installation on macbook,without a cdrom..intel mac..."
date: 2009-04-18
forum: Apple Hardware Users
---

### Post by akshay.sulakhe on 2009-04-18
Hello friends...I have a macbook and i want to install ubuntu on it..i have done that quite a few times before...but now this time i dont have a cdrom for installation,so i once tried with a USB cd rom(read dvd rom)...it gave me some USB reset error,when i googled it up,thats a kernel error and is persistent since a long period...so is there any way i can install ubuntu on macbook....Mine is a Intel mac...Thanks..

---

### Post by pxwpxw on 2009-04-18
> **akshay.sulakhe said:**
> Hello friends...I have a macbook and i want to install ubuntu on it..i have done that quite a few times before...but now this time i dont have a cdrom for installation,so i once tried with a USB cd rom(read dvd rom)...it gave me some USB reset error,when i googled it up,thats a kernel error and is persistent since a long period...so is there any way i can install ubuntu on macbook....Mine is a Intel mac...Thanks..

You might like to try this draft procedure - which is also useful for MacBookAir.

But what is your MacBook model? (About this mac - more ) - important for some details.
----------------
The network install method does not need a CD, only an internet connection.
When there is no existing linux install with grub-pc, it uses the grub2 grub.efi bootloader .This is an EFI bootloader which can be installed on the Mac OSX partition.
----------------
This is how -

1. Download install and try rEFIt latest version which all intel macs should have for linux.
  rEFIt is from refit website [http://refit.sourceforge.net/](http://refit.sourceforge.net/)

2. Download install grub.efi bootloader which finally can boot (from command line) the linux and initrd.gz installer, all from the OSX partition.

  grub2 EFI bootloader thread
   [http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)
[Post523]("http://ubuntuforums.org/showpost.php?p=6966036&postcount=523") has grub.efi attachments for download.

3. Download the Net Boot Installer 'linux' and 'initrd.gz' files - (this is for intrepid i386, change for jaunty or amd64 if you want)
 
[ubuntu-intrepid-i386-netinstall ]("http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/ubuntu-installer/i386/")

4. Move grub.efi and the installer linux and initrd.gz up to the top (root) of the OSX partition.

5. Boot grub.efi using rEFIt, then from the grub> command line, boot the installer.
This is for i386 kernel and MacBook2,1.
```

grub> search /linux
grub> search --set /linux
grub> linux /linux video=efifb acpi=force
grub> initrd /initrd.gz
grub> boot

```
For  amd64 install kernel may need to use for the linux command
grub> linux /linux video=efifb acpi=force   noefi
and may need to add at the first line
grub> fakebios
--------------

All the files are small.

The Net installer images can then download all the ubuntu installation from the internet.

If you get those files downloaded to your OSX and refit installed and working, we can take it from there, just needs to boot the installer with grub.efi - but details may depend on the mac model.

===================

---

### Post by akshay.sulakhe on 2009-04-18
Thank u very much..i will surely do it...i have an intel mac 2,1...thats what i know...i already have refit installed...i prefer it because it helps me in easy booting...again thank u very much...

---

### Post by pxwpxw on 2009-04-18
> **akshay.sulakhe said:**
> Thank u very much..i will surely do it...i have an intel mac 2,1...thats what i know...i already have refit installed...i prefer it because it helps me in easy booting...again thank u very much...

I just rechecked on my MB21 for the intrepid i396 and jaunty amd64 installer and the grub.cfg menu below works for both, and gives a grub boot menu, so you dont need to use the grub> commandline.

If you do run the commands from the grub> commandline, add the grub> boot command.

Copy to a textfile named grub.cfg and put beside grub32.efi, this will give a boot menu.

```

#grub.cfg
timeout=20
default=0
set F1=ctrl-x

menuentry "netinstall" {
	fakebios
	search --set  /linux
	linux  /linux video=efifb acpi=force
	initrd  /initrd.gz
}

```
function key  F1 will boot from 'e' edit if editing menuentry in grub.

---

### Post by mzyatas on 2009-08-17
Thanks for this.  Worked nicely on my macbook without a working cdrom!

---

### Post by &#1103;&#1091;&#1076;&#1080; on 2009-08-18
I just installed jaunty on my 2nd Gen MacBook yesterday and I would write step by step what I did but I used the install disk I made.

Good Luck anyway mate.

---

