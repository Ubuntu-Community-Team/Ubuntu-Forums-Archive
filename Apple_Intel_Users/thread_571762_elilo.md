---
title: "elilo"
date: 2007-10-09
forum: Apple Intel Users
---

### Post by johndela1 on 2007-10-09
Is anyone here using elilo?

---

### Post by cyberdork33 on 2007-10-09
not many since you cannot fully use 3d graphics when booting from EFI.

---

### Post by johndela1 on 2007-10-10
Doesn't apple's video card support efi?  I mean the mac uses efi

---

### Post by cyberdork33 on 2007-10-11
> **johndela1 said:**
> Doesn't apple's video card support efi?  I mean the mac uses efi

It is obviously possible, but Apple has not clued in the Linux community on how to do things appropriately. Right now, it is standard practice to use the BIOS compatibility in mactels to run linux. You can get linux to boot with elilo, there are just graphics issues.

From the rEFIt '[Myths & Facts]("http://refit.sourceforge.net/myths/")' page:
> 
**Fact: You need BIOS compatibility for 2D/3D accelleration**

  If you want good graphics support in Linux, you must boot it using BIOS compatibility mode. This also means using LILO or GRUB, and having a MBR partition table (either hybrid GPT/MBR or plain MBR). 
  The X.org / XFree86 drivers for Intel and ATI hardware require a Video BIOS to initialize the card. The Linux text console also relies on the Video BIOS. Apple&#8217;s firmware only provides a Video BIOS when booting in BIOS compatibility mode. Without it, you only get unaccellerated frame buffer graphics. 
  Side note: James McKenzie published a [hack to elilo]("http://www.madingley.org/macmini/") that activates the Video BIOS without activating the full BIOS compatibility mode. This actually allows the accelerated drivers to work without booting through LILO/GRUB. Unfortunately it only works on the Mac mini and hasn&#8217;t been updated in months.

---

### Post by pxwpxw on 2007-10-12
> **cyberdork33 said:**
> It is obviously possible, but Apple has not clued in the Linux community on how to do things appropriately. Right now, it is standard practice to use the BIOS compatibility in mactels to run linux. You can get linux to boot with elilo, there are just graphics issues.

From the rEFIt '[Myths & Facts]("http://refit.sourceforge.net/myths/")' page:

And also from rEFIt Myths and facts

> 
**Myth: You need BIOS compatibility to boot Linux**

While it is very common (and recommended) to boot Linux using BIOS compatibility mode and LILO/GRUB, there are other ways to boot Linux on an Intel Mac.

Even before Boot Camp was released, elilo (the EFI Linux Loader) was used to boot Linux on Intel Macs. However, this requires a specially prepared kernel and has some drawbacks (like not having 2D/3D accellerated graphics, see below).


As in the Mac Mini hack, it looks as if a special kernel is needed to even get a system running, before thinking about graphics refinements.

There does not seem to be a usable elilo package for current ubuntu releases and Apple efi on the MacBook.

It seems to be available with ia86 itanium packages.

I have tried but failed to even get as far as loading an elilo configuration menu - that is before any kernel considerations. 

I would also like to know if anyone in this forum has elilo in use.

---

### Post by ronocdh on 2007-10-12
> **pxwpxw said:**
> I would also like to know if anyone in this forum has elilo in use.
I'm for sure still using GRUB. IIRC, I believe benanzo had switched to ELILO pretty early on, but I don't know whether that still holds true.

---

