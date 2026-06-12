---
title: "Help with GRUB-EFI on MacBook Pro 5,1"
date: 2010-08-24
forum: Apple Hardware Users
---

### Post by SwedishWings on 2010-08-24
I'm stuck... hope someone can help me out.

I have compiled GRUB 1.98 from source ([ftp://alpha.gnu.org/gnu/grub/grub-1.98.tar.gz](ftp://alpha.gnu.org/gnu/grub/grub-1.98.tar.gz)) with:

```
./configure --with-platform=efi --target=x86_64
make

```

created a boot image with 

```
./grub-mkimage -d . -o grub.efi part_gpt hfsplus fat ext2 normal sh chain boot configfile linux

```

then copied all files to my mac partition under /efi/grub (where a working copy of refit resides):

```
sudo cp grub.efi *.mod *.lst /efi/grub
```

grub.cfg has two entries:

```
menuentry "Linux 1" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 4defee49-30ae-437c-977d-e9022d3f9700
	fakebios
#	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=4defee49-30ae-437c-977d-e9022d3f9700 ro quiet splash video=efifb noefi
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=4defee49-30ae-437c-977d-e9022d3f9700 video=efifb noefi acpi=force
	initrd	/boot/initrd.img-2.6.32-24-generic
}

menuentry "Linux 2" {
  insmod ext2
  setroot='(hd0,4)'
  search -f /vmlinuz
  fakebios
  linux /vmlinuz root=/dev/sda4 video=efifb noefi
  initrd /initrd.img
}
```

Refit finds the grub files and loads them properly. Once i get to the grub menu and select any of the two entries there this happens:

When i try to boot "Linux 1" it hangs with the screen in attachment 1.

When i try to boot "Linux 2" it hangs with the screen in attachment 2.

Any help to get on with this is most welcome.

Thanks!

/Mike

---

### Post by Sidolin on 2010-08-24
The important bits from my grub.cfg:

> insmod efi_gop
insmod font
loadfont (hd1,gpt5)/boot/grub/unicode.pf2
insmod gfxterm
set gfxmode=1680x1050x32
set gfxpayload=1680x1050x32

> 
menuentry 'Ubuntu, with Linux 2.6.36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set 411d65e5-b905-4367-b393-1d007261d36e
	loadbios /boot/vbios.bin /boot/int10.bin
	linux	/boot/vmlinuz-2.6.36-rc2-mbp+ root=UUID=411d65e5-b905-4367-b393-1d007261d36e noefi single i915.modeset=0 i915.powersave=0 
	initrd	/boot/initrd.img-2.6.36-rc2-mbp+
}


Also see [http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

---

### Post by SwedishWings on 2010-08-24
> **Sidolin said:**
> linux /boot/vmlinuz-2.6.36-rc2-mbp+

Thanks!

Did you have to compile a new kernel to make this work?

---

### Post by metatechbe on 2010-08-25
SwedishWings,

I have the same output as you when I boot on the 9400M :
```
ROM image is present
   [Linux-bzImage, setup=0x3400, size=0x3d56c0]
   [Initrd, addr=0x3f7fff000, size=0x7f0349] 

```

By adding more debugging code in grub-efi, I see that the "grub_efi_locate_protocol" succeeds, but the "get_mode" fails with return code  GRUB_EFI_NOT_READY (6).
So it looks like the locate_protocol finds the card that is disabled...

When I boot on the 9600M GT I get the output
```
ROM image is present
   [Linux-bzImage, setup=0x3400, size=0x3d56c0]
Video mode: 1440x900-32@0
Display Controller: 2:0.0
Device id: 64710de
MMIO(0): 0xe4000000
VMEM(1): 0xc0000000
MMIO(3): 0xe2000000
Frame buffer base : 0xc0030000
Video line length: 8192
   [Initrd, addr=0x3f7fff000, size=0x7f0349] 


```

By the way, this output is another way to get the FrameBufferBase ("Frame buffer base") and "PixelsPerScanLine" ("Video line length"/4)

Regards,

metatech

---

