---
title: "EFI gone?"
date: 2008-05-07
forum: Apple Hardware Users
---

### Post by niteblind on 2008-05-07
Hi All,

I managed to delete the EFI partition (as I understand it this is the 200mb system partition) which I apparently need to have for firmware updates and so on.

Does anyone know how I can try and get this back? I tried just reinstalling the OSX cd but it did not put it back on the options I chose so does anyone know? My fan on the macbook seems to be on a lot more since this was deleted so I really think I need it.

cheers for any assistance you can provide.

niteblind

---

### Post by cyberdork33 on 2008-05-07
The only way I have been able to do it is do a complete format of the drive in Disk Utility. You might be able to define one with parted (or gparted).

---

### Post by niteblind on 2008-05-07
> **cyberdork33 said:**
> The only way I have been able to do it is do a complete format of the drive in Disk Utility.

As far as my experience has gone this does not replace the EFI partition simply installs OSX ontot he drive without the EFI partition which is where I am at currently. I called Apple and the tech in India did not reall know what he was on about before I got cut off.

niteblind

---

### Post by thenes on 2008-05-08
I have not done this with os x 10.5, so I am not quite sure if what I say is true, but I think there is a difference between simply reinstalling the system via the os x system CD on the one hand, and on the other hand using Disk Utility on the system CD to first format the drive and then install os x from the CD.

If this is correct however, it would be a valid question to ask if you used Disk Utility on your live CD, or if you simply did a clean install of the system according to the default setup.

---

### Post by cyberdork33 on 2008-05-08
> **thenes said:**
> I have not done this with os x 10.5, so I am not quite sure if what I say is true, but I think there is a difference between simply reinstalling the system via the os x system CD on the one hand, and on the other hand using Disk Utility on the system CD to first format the drive and then install os x from the CD.yep that is what I was trying to say earlier.

---

