---
title: "How do you verify CRC32 checksums of files?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by chaoswings on 2007-09-23
In windows I used a program called hashcalc to verify the checksums of the files I downloaded..found here

[http://www.slavasoft.com/hashcalc/index.htm](http://www.slavasoft.com/hashcalc/index.htm)

Is there any program out there that supports all the popular hash and checksum algorythims?

---

### Post by jamvegan on 2007-09-23
The most common type of checksum that I see is md5.  For verifying those I use md5sum (which I believe is installed by default).  I was not familiar with CRC32, so I opened Synaptic and did a search for it (using "Look in: Description and Name") and found a utility called cksfv which "uses crc32 checksums to verify that files are intact" (which is not installed by default).  Hope that helps!

---

### Post by chrome307 on 2007-09-23
ChkSFV is a command line tool and you have to run it via Terminal.

Alternatively if you running WINE you can use QuickSFV for a GUI based application.

---

### Post by chaoswings on 2007-09-26
thanks

---

