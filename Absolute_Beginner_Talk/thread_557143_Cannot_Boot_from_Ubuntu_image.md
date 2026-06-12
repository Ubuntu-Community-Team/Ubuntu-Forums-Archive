---
title: "Cannot Boot from Ubuntu image"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by kozmo on 2007-09-22
I downloaded the Ubuntu Server 7.04.
Start both vmware and virtual box and pointed to the Ubuntu iso.

Both vmware and virtual box tells me the image is not bootable.

So I used nero to burn the image to a CD, I can see all of the files on the CD, but I still get the same message from vmware and virtual box -- it is not bootable.

What do you have to do to load this OS???

---

### Post by tie_dyed_sox on 2007-09-22
Even though you can browse the CD, there might be a problem with the boot sector (???)

To start with, I'd make sure that the MD5 checksum of the .iso is correct...
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Check it against the corresponding hash for Ubuntu Server 7.04...
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If the hashes don't match, you'll have to download it again.

If the image file is ok, try rebooting your PC with the CD in the drive (making sure you have the drive as first bootable device in your BIOS). If that works then it's likely that VMWare/Virtual Box have  issues  - Afraid I can't offer much help there.

Hope this helps.

---

### Post by kish on 2007-09-22
I had the same problem sometime back

"I used nero to burn the image to a CD"

Mistake was I burned the iso as a data project instead of burning the image.

---

### Post by tie_dyed_sox on 2007-09-22
> **kish said:**
> I had the same problem sometime back

"I used nero to burn the image to a CD"

Mistake was I burned the iso as a data project instead of burning the image.

Oops! I've made that mistake a few times as well! :oops:

---

