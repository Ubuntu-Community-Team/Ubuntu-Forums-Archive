---
title: "Burning Snow Leopard DMG on Ubuntu"
date: 2012-09-01
forum: Apple Hardware Users
---

### Post by LunaMacNoob on 2012-09-01
I'm running Ubuntu 12.0.4 and am trying to burn a SL DMG of Snow Leopard onto a blank DVD. Every time I attempt this however,  it shows this message

The size of the file is over 2 GiB. Files larger than 2 GiB are not supported by the ISO9660 standard in its first and second versions (the most widespread ones).
It is recommended to use the third version of the ISO9660 standard, which is supported by most operating systems, including Linux and all versions of Windows™.
However, Mac OS X cannot read images created with version 3 of the ISO9660 standard.

How will I overcome this so my DVD is bootable on my iMac. I'm currently running Ubuntu on the iMac

Thanks

---

### Post by Lars Noodén on 2012-09-01
I've been looking for a way to do this and been trying myself.  Many instructions seem to rely on [dmg2img](http://manpages.ubuntu.com/manpages/precise/en/man1/dmg2img.1.html) but that is not working for me.  There is also a tool [dmg2iso](http://blinkenlights.ch/gnupod/dmg2iso.pl) floating out there too, at Blinkenlights.  But I had no luck with my image and got various errors.  Perhaps they work with your image, though.

---

### Post by LunaMacNoob on 2012-09-01
> **Lars Noodén said:**
> I've been looking for a way to do this and been trying myself.  Many instructions seem to rely on [dmg2img](http://manpages.ubuntu.com/manpages/precise/en/man1/dmg2img.1.html) but that is not working for me.  There is also a tool [dmg2iso](http://blinkenlights.ch/gnupod/dmg2iso.pl) floating out there too, at Blinkenlights.  But I had no luck with my image and got various errors.  Perhaps they work with your image, though.
I've solved it now. Turns out you can wine run Transmac

---

