---
title: "Creating Ubuntu CD in Toast"
date: 2006-07-27
forum: Apple PPC Users
---

### Post by timka1 on 2006-07-27
I think this is probably the right forum for this post - apologies if not - but it's a problem that starts on the Mac but ends on a PC...

I have OSX 10.4 running on iMac G5 (love it!) but I am trying to put Ubuntu onto an old PC to get a feel for Linux and because it will hopefully be more secure and stable than Windows XP. I downloaded the 386 installation CD image to the iMac and it loaded as a new volume. I then burnt it to CD using Toast using the ISO9660 option.

However when I put it in the PC to boot and selected CD as boot device I got a boot failure. Should I reburn in a different format or do I need to change the BIOS in some way to expect Linux?

---

### Post by bogoliubov on 2006-07-27
You shouldn't need to change anything in the BIOS just for Linux, just as long as you make sure the CD is the first in the "boot-order". If it doesn't work; check if the CD-ROM unit is working. As for filesystem, I don't know. If you have checked the other things and it still doesn't work; try to change the ISO format...

---

### Post by timka1 on 2006-07-27
I know the CD drive works as a boot device because I can get the XP Install CD to boot.

So it looks like I need to burn the CD again. I think I'll try burning it on the PC itself...

---

### Post by linear on 2006-07-27
You need to burn the iso as an **image **to the CD - if you're picking a format, then you're in the wrong place.

---

### Post by timka1 on 2006-07-27
Reporting back as promised:

And it's good news! I created a working Ubuntu boot CD.

The path I took (not the only one I suspect) was to transfer the .iso file onto a mobile hard disk and then copy it to the PC which was recognised by Easy CD Creator which burnt it to CD (the default action).

I now have rebooted and a promising new OS is dawning on territory that has only seen Windows before!

Looking forward to it!

---

### Post by timka1 on 2006-07-27
> **linear said:**
> You need to burn the iso as an **image **to the CD - if you're picking a format, then you're in the wrong place.

Only just saw this helpful post.

To be thorough I looked into this and you're absolutely right if I drag the .iso file onto Toast app it opens and says it is copying an image file.

The mistake I was making was that the image file had been opened/mounted by OSX automatically (helpful as always!) and so I was copying the contents of a volume rather than the image and that was what was wrong I guess...

Thanks for post.

---

