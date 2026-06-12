---
title: "Live CD on Mac won't boot back to Mac OS"
date: 2010-09-17
forum: Apple Hardware Users
---

### Post by kgmeyer4995 on 2010-09-17
To get my Intel based mac to boot live CD, I changed setting so that CD would be boot device.  I was able to successfully launch the lucid lynx live CD.  However, I couldn't figure out how to return to Mac OS boot off the hard drive since the default boot drive had been switched.  I just figured the system would cycle through the drives until it found the Mac OS boot drive.  It didn't.  It kept looking for a bootable disk in the CD drive.  What is the right was to restore the system to Hard disk boot since the original change was made in Mac OS?

I was able to fix the problem after some panic by using the Mac OS install utility disc.  Even that was convoluted though.  I'm sure there's a right way to do this and I would like to understand it.
K

---

### Post by garvinrick4 on 2010-09-17
> **kgmeyer4995 said:**
> To get my Intel based mac to boot live CD, I changed setting so that CD would be boot device.  I was able to successfully launch the lucid lynx live CD.  However, I couldn't figure out how to return to Mac OS boot off the hard drive since the default boot drive had been switched.  I just figured the system would cycle through the drives until it found the Mac OS boot drive.  It didn't.  It kept looking for a bootable disk in the CD drive.  What is the right was to restore the system to Hard disk boot since the original change was made in Mac OS?

I was able to fix the problem after some panic by using the Mac OS install utility disc.  Even that was convoluted though.  I'm sure there's a right way to do this and I would like to understand it.
K A normal BIOS gives you the selection to put HDD first or USB or CD if nothing in either USB or CD should boot off of HDD if usb and cd are ahead of HDD. Can put in any order in BIOS.
 There is also the option in BIOS to pick which drive you want to boot from. Like CENTON USB or whats in CD or the name of HDD. Mine is hitting escape key for menu. Some are hitting F10 or others F2. Or ask in Mac forum in here and sure a lot of users will answer quick.

---

### Post by kgmeyer4995 on 2010-09-18
Rick,
Thanks for the advice.  I'm pretty knowledgeable on BIOS for PC's but not Mac's.  I'll have to look into that on the Apple forums.  I familiar with setting the boot order for devices through BIOS on PC so once I get in, I should be in good shape.
K

---

### Post by kgmeyer4995 on 2010-09-18
Rick,
I did a little more homework.  Although Mac's have firmware that performs BIOS functions, the Mac folks prefer to call it firmware.  It appears to be command line driven.  To access the command line on newer Intel based macs you have to hit a key sequence during boot.  There a good description at [URL="http://answers.yahoo.com/question/index?qid=20081022091127AAxqu0y"].  You are able to set the boot sequence from there.
Kevin

---

### Post by garvinrick4 on 2010-09-18
Read your site on getting into MAC Bios or firmware. It was good to know thanks for posting.

---

### Post by linuxopjemac on 2010-09-18
that trick only works for NewWorld PowerPC based Macs, not the newer Intel ones.

---

### Post by garvinrick4 on 2010-09-18
> **linuxopjemac said:**
> that trick only works for NewWorld PowerPC based Macs, not the newer Intel ones.
What is the your Intel style? Is nice to know these things for reference.

---

### Post by linuxopjemac on 2010-09-18
There is no way to do that in Intel Macs.

---

