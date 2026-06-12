---
title: "EFI boot hardy"
date: 2008-08-19
forum: Apple Hardware Users
---

### Post by dranfi on 2008-08-19
Well, I have a 5-boot working (Leopard, XP (32 bits, SP3) ,Vista (32 bits, SP1), Ubuntu (32 bits, 8.04) and Fedora (64 bits, 9)) on my MacBook C2C 2,1; GPT/MBR hybrid partitioning.
I have my grub (the one included in Ubuntu) installed on my OS X partition.
I'm using rEFIt. I started paying with GRUB2, version EFI. Now I can chainload OS X, but I can't load Ubuntu, my kernel is 2.6.24-19-generic.
I think that I should recompile a newer kernel in order to have EFI support?
Can you give me the instructions and/or .config file? Not forgetting the kernel args.

Thank you in advance.

---

### Post by cyberdork33 on 2008-08-19
You have to enable EFI bootability in the kernel. I think this is on by default in 2.6.26 (i.e. Intrepid might work)

---

### Post by pxwpxw on 2008-08-19
You need 2.6.25 or 2.6.26.

The current linux-image from the intrepid packages is good for grub.efi,
just install the package, no need to reconfigure. I am using it or the
2.6.26-4-generic from intrepid server install cd.


admax@WDC:~$ uname -a
Linux WDC 2.6.26-4-generic #1 SMP Mon Jul 14 18:39:53 UTC 2008 i686
GNU/Linux
admax@WDC:~$

I will post my config info tomorow, its a bit late now.
Good to see someone else using grub.efi

---

### Post by dranfi on 2008-08-19
Well I tryed with that kernel (32 bits), my EFI firmware is 32 bit and I have an horrible screen : [http://www.megaupload.com/fr/?d=B3YZ2AM3]("http://www.megaupload.com/fr/?d=B3YZ2AM3").
My grub.efi is capable to load a 64 bits Fedora kernel but is has a lot of ata1.00 errors.

---

### Post by cyberdork33 on 2008-08-19
graphics do not work well under an EFI boot. This is a known limitation.

---

### Post by dranfi on 2008-08-19
I that case, it's not a limitation, but it's unusable!

---

### Post by cyberdork33 on 2008-08-19
> **dranfi said:**
> I that case, it's not a limitation, but it's unusable!
I say that because it really depends on what Mac you use. You can even get 3d acceleration going on Mac Minis. This is the biggest obstacle so far in getting a good EFI-boot solution for Linux on Macs.

---

### Post by pxwpxw on 2008-08-20
> **dranfi said:**
> I that case, it's not a limitation, but it's unusable!

In your screen picture .jpg, the "venetian blind" with 10 columns is just an indication that some tweaking of kernel boot args and blacklist is needed.

I have seen that many times until fixed.

It requires agp off and use of framebuffer (fbdev), so if you can't live without agp, thats the end of the story, but if you can then see my next post.

---

### Post by pxwpxw on 2008-08-20
===============================
Tweaks for grub.efi booting  MacBook c2d.

1. grub.cfg menuentry (extracts )

```

menuentry "search-2.6.26-4-generic sdb2 X" {
	search --set  /boot/vmlinuz-2.6.26-4-generic
 linux  /boot/vmlinuz-2.6.26-4-generic root=/dev/sdb2 ro agp=off video=efifb 
 initrd  /boot/initrd.img-2.6.26-4-generic
}
menuentry "search-2.6.26-4-generic sdb2 SINGLE" {
	search --set  /boot/vmlinuz-2.6.26-4-generic
 linux  /boot/vmlinuz-2.6.26-4-generic root=/dev/sdb2 ro single agp=off video=efifb 
 initrd  /boot/initrd.img-2.6.26-4-generic
}

###  one custom kernel needed the pci=bioisrq for ATA error,  bug not seen since, (hint was in syslog/dmesg)
 
menuentry "search-2.6.26-efi01 sda4 -SINGLE" {
	search --set  /linux/vmlinuz-2.6.26-pxw-efi-01
 linux  /linux/vmlinuz-2.6.26-pxw-efi-01 root=/dev/sda4 ro single video=vesafb agp=off pci=biosirq
 initrd  /linux/initrd.img-2.6.26-pxw-efi-01
}

```

2. Use the single user root console startup until all clear to run the Desktop.
 You can edit your ubuntu system from another linux or rescue cd (if you cant boot it with a non-efi bootloader).

## console needs the fbcon module, this intrepid install had it, if not, you may get a blank console screen, you have to edit /etc/modules and add fbcon - probably from the rescue cd, or other system (and later add to /etc/initramfs-tools/modules and update-initramfs).

4. /etc/X11/xorg.conf needs the Driver "fbdev", no other change if it was working before.
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"fbdev"
EndSection

```

5. additions to /etc/modprobe.d/blacklist - required.  
```

blacklist agpgart
blacklist intel-agp

```

6. I am using grub.efi made by grub-mkimage compiled from the grub2  gnu source, not the ubuntu grub2 packages.

  [http://svn.savannah.gnu.org/viewvc/trunk/grub2/?root=grub](http://svn.savannah.gnu.org/viewvc/trunk/grub2/?root=grub)

7. grub.efi and grub.cfg are in an hfsplus partition#1 on this external enclosure,
intrepid is on ext3 #2. (I also have grub.efi  in various hfsplus parts on the MacBook hd, with Macosx on sda2 and xubuntu804 on sda3/4).
The external is /dev/sdb and has MBR partitioning.

```

(parted) p free                                                           
Model: WD 3200AAJS Externa (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  7151MB  7151MB  primary  hfs+              
        7151MB  7156MB  4841kB           Free Space        
 2      7156MB  47.1GB  40.0GB  primary  ext3         boot 
 3      47.1GB  49.1GB  1999MB  primary  linux-swap        
        49.1GB  320GB   271GB            Free Space        

```

8. Previous related post and links

  [http://ubuntuforums.org/showpost.php?p=5579534&postcount=16](http://ubuntuforums.org/showpost.php?p=5579534&postcount=16)

---

### Post by pxwpxw on 2008-08-21
on my macbook (see below): 

 grub.efi from the ubuntu grub-efi package :

	grub-efi_1.96+20080512-1ubuntu2_i386.deb

		is broken. 

grub.efi made with all modules and installed manually fails
to load ubuntu kernels 

 vmlinuz-2.6.26-5-generic
 vmlinuz-2.6.26-5-generic
 vmlinuz-2.6.25-1-386
 and others.

and has bugs in its command line.

It does manage to chainload macosx.

Use grub.efi made by grub-mkimage compiled from the grub2 gnu source, it works.

[http://svn.savannah.gnu.org/viewvc/trunk/grub2/?root=grub](http://svn.savannah.gnu.org/viewvc/trunk/grub2/?root=grub)

Platform:
# dmidecode -t system
# dmidecode 2.9
# SMBIOS entry point at 0x3eebf000
SMBIOS 2.4 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Apple Inc.
	Product Name: MacBook2,1
	Version: 1.0
	Serial Number: W8717FYXWGL
	UUID: 61F9E18A-38B2-B440-A87E-7457DF18863C
	Wake-up Type: Power Switch
	SKU Number: System SKUNumber
	Family: MacBook

Handle 0x0004, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x0106, DMI type 12, 5 bytes
System Configuration Options

Running kernel loaded by grub.efi (svn)

# uname -r
2.6.25-1-386

I have submitted a bug report on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/259986/](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/259986/)

---

### Post by cyberdork33 on 2008-08-21
> **pxwpxw said:**
> I have submitted a bug report on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/259986/](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/259986/)
Now's the time to get them in. I have noticed a lot of the mactel bugs are getting assigned to devs recently, probably for inclusion to Intrepid. Still nothing on the MBR clearing bug though :(
[https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/222126](https://bugs.edge.launchpad.net/ubuntu/+source/ubiquity/+bug/222126)

---

