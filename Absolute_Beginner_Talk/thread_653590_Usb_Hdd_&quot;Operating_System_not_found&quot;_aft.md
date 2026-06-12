---
title: "Usb Hdd &quot;Operating System not found&quot; after Gutsy Gibbon install."
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by sulpherdragon on 2007-12-30
Ok, i have 1 laptop, 1 external usb hdd and 1 gutsy gibbon cd.

ive removed the internal hdd of the laptop so all i have is the external drive running from usb.

ive tried a lot already, but most recently ive made a an 18gb ext3 partition and a 2gb swap partition. after the installation i try to boot from the usb drive an i get "Operating System not found".

Is grub not going onto the disk?!

Yes ive read other threads and followed walkthroughs but its still not going right for me.
if someone could tell me where im going wrong id love to know please.

---

### Post by Liolikas on 2007-12-30
Why you removed internal hdd?

Better use internal hdd.

Not all bios'es allow booting from usb at all. So you will have to use boot from fdd and other not funny stuff.

---

### Post by LaRoza on 2007-12-30
Not all computer can boot from USB. And it is pretty spotty at times.

It seems your BIOS can't find an operating system (that is what the error's source, the BIOS)

You can enter the BIOS setup and try to set USB as a boot device, but in the absence of any other boot device, it didn't find it, so I doubt it will work.

---

