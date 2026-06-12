---
title: "Is Mactel's macfanctld necessary in 13.04?"
date: 2013-02-08
forum: Apple Hardware Users
---

### Post by cole.mickens on 2013-02-08
Hi.

13.04 works great on my Macbook Air 2012 with two caviats:

1. I don't know if the fans will turn on automatically. The mactel-support/ppa isn't available. Is my MBA going to melt?

2. The EFI boot is still broken. The default ISO boots just fine, but after the install, the EFI boot is broken. Obviously, the +mac ISO works but it uses BootCamp/BIOS boot.

Any thoughts on either issue? Thanks!

---

### Post by Garlandg on 2013-02-09
For the EFI booting, you might consider using rEFInd.  I wrote a guide for the Retina Mac, located [COLOR=Blue][here <Link>]("http://linuxmacbookproretina.blogspot.com/")*[.]("http://linuxmacbookproretina.blogspot.com/")*[/COLOR]  The rEFInd install instructions should work if you can boot your mac into Linux already.  It's not too difficult to do.

---

### Post by cole.mickens on 2013-02-09
> **Garlandg said:**
> For the EFI booting, you might consider using rEFInd.  I wrote a guide for the Retina Mac, located [COLOR=Blue][here <Link>]("http://linuxmacbookproretina.blogspot.com/")*[.]("http://linuxmacbookproretina.blogspot.com/")*[/COLOR]  The rEFInd install instructions should work if you can boot your mac into Linux already.  It's not too difficult to do.

Yeah! I ran into it yesterday while Googling, but at that point I'd given up and reloaded it with BIOS mode so REFIND won't install itself now. I'll probably boot off the regular ISO and try to install REFIND.

(Plus I can fix the blessing issue, it's so stupid that Apple can't just make a proper UEFI implementation...)

On a good note-- the fans seem to work. I kinda forgot about being worried about it and fired up Counter Strike: Source. Few minutes later the fans are blaring as expected.

Cheers. I'll let you know how REFIND goes. Thanks for the guide!

---

### Post by cole.mickens on 2013-02-10
> **Garlandg said:**
> For the EFI booting, you might consider using rEFInd.  I wrote a guide for the Retina Mac, located [COLOR=Blue][here <Link>]("http://linuxmacbookproretina.blogspot.com/")*[.]("http://linuxmacbookproretina.blogspot.com/")*[/COLOR]  The rEFInd install instructions should work if you can boot your mac into Linux already.  It's not too difficult to do.

A big Thank You! rEFInd did the trick. I wiped the whole thing, installed OS X. Disabled the startup chime, installed rEFInd. Resized OS X to make room for Ubuntu. Booted the Ubuntu installer from EFI mode and then just did a standard install putting Ubuntu in the gap I made in OS X. Additionally, leave the bootloader option alone, it knows to install the efi binarified version of grub into the system efi partition.

Much less painful than in the past. Finally, easy native dual boot on Macbooks without BIOS emulation and BootCamp.

Woot!

---

### Post by wilberfan on 2013-05-05
> **cole.mickens said:**
> Hi.

13.04 works great on my Macbook Air 2012 with two caviats:

1. I don't know if the fans will turn on automatically. The mactel-support/ppa isn't available. Is my MBA going to melt?  

Any thoughts on issue #1?  I just upgraded from 12.04 to 13.04.  I had macfanctld installed on 12.04...   Does anyone think it's a good idea on 13.04, or have any fan issues been addressed in this release?

---

