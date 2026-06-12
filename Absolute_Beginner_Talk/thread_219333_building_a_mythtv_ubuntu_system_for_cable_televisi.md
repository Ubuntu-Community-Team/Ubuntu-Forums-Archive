---
title: "building a mythtv ubuntu system for cable television"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-07-19
i want to use the hauppauge wintv-pvr-500 mce-kit.
The traget system will be a PIII 933 512 megs of ram
Ubuntu will be installed to a 20 gig hard drive
i'll install a 300 gig seperate drive on a pci controller card.
Will this work?? Also i assume the hauppauge will provide output to the tv set?

---

### Post by crispy_420 on 2006-07-20
That card does not support TV-out.

I believe that the PVR-350 has a hardware decoder. That card, the 500, only has hardware encoding. 

For your needs try picking up a NVidia card with TV-out. You can find one for your needs, either PCI or AGP. You'll also find plenty of guides here on these forums for NVidia setup as well.

I have this card myself, although not used in linux (WinXP with SageTV). But I do have an extra computer with WinXP Media Center that I have not booted in months and I have been considering this myself. Here are my specs:

> Intel Celeron 2.8GHz - 533MHz FSB
512MB DDR
NVidia MX440
Haupaugge PVR-150 MCE Low Profile
80GB Seagate Hard Drive
ASUS Micro-ATX

I may decide to do this project myself soon. Either that or I may tryout [SageTV]("http://sagetv.com/linuxOEMedition.html") for linux. That also looks like a good option if you want to avoid Windows. The downside is cost, it is around $80(US). But I will try the ubuntu option first. Just need the time to do a new project that I am unfamiliar with, but it is so hard to get away from BF2.

---

### Post by nalmeth on 2006-07-20
That card seems supported in linux, but as for TV, the previous poster is probably correct, you'll need to pickup an extra video card for TV-out.

If you don't need 3D-acceleration, you can likely grab one for really cheap.

Your hardware specs look fine otherwise

---

### Post by crispy_420 on 2006-07-20
Even the cards for 3D acceleration are cheap these days. I'm not talking about a mind blowing card but rather something kind of basic. You will want an NVidia based card and not an ATI, I hear ATI's drivers just plain suck for TV-out.

Here's some cheap ones if you live in the US or maybe even Canada. But if not you could just try and track down the same/similar models in your area.

[NVidia based AGP]("http://www.newegg.com/Product/ProductList.asp?N=2010380048+1305520548+4093&Submit=ENE&SubCategory=48")

[NVidia based PCI]("http://www.newegg.com/Product/ProductList.asp?SrchInDesc=S-Video&Page=1&N=2010380048+1305520548+1069609642&Submit=ENE&Nty=1&SubCategory=48")

***** I kinda a fan of newegg *****

Based on your specs, PCI Express is not an option. But you would need that kind of power for this type of project. And stay away from odd chipsets that are not NVidia based, they may say TV-out but only in windows.

You should consider posting something of this nature in Video & Sound sub forum. You will more likely get some better feedback from people that spend more time with this kind of thing.

---

