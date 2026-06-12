---
title: "Checksum or similar for iso downloads?"
date: 2007-01-22
forum: Apple PPC Users
---

### Post by gurnemanz on 2007-01-22
What utility is used to check our pre-burn iso downloads? I've been making a lot of coasters this last week. The Pismo won't boot from anything, even with the use of older media and a new old-stock previously unused internal SuperDrive.

There's a credible rumor of a stack of hot Taiyo Yuden cd blanks coming into town this week, heh-heh-heh . . . ](*,) 

It's called something other than 'checksum' under Windows, but the idea is the same - to do a mathematical verification that what you've downloaded is what started out uploading on the other end.

Thanks!

---

### Post by yabbadabbadont on 2007-01-23
Usually in Linux, md5sum is used.

---

### Post by gurnemanz on 2007-01-23
> **yabbadabbadont said:**
> Usually in Linux, md5sum is used.

Can this be run in OS X? It's the old problem of not having a Linux environment in which to check the checksum, since the installer package is what has to be checked.

If I'm missing something obvious, please do relieve my ignorance. Ignorance is why I'm here.

---

### Post by grazie on 2007-01-23
The tool is called md5 on OS X. Does the exactly the same.

$ md5 <filename>.iso

and compare the number output to what is expected.

---

### Post by yabbadabbadont on 2007-01-23
Also, I think the Ubuntu cds all have an option on the boot menu to run an integrity check of the cd that is currently booted.

---

### Post by liberty4u on 2008-01-20
For easy to follow step by step instructions just enter this string of terms in your favorite search engine:

linux iso integrity checksum md5

that answered the question for me...  :guitar:

---

### Post by simplekoala on 2008-05-12
Hello

Does anyone know where I can find MD5 hashes for recent Xunbuntu PPC ports.  Maybe I'm being stupid but I cant seem to find them.
Thanks

-S

---

### Post by childofGod on 2008-05-12
I downloaded Hardy as an iso and then burned it to cd without running md5sum (unaware of it at the time).  When I went to install it hung up at forty percent and then bounced due to errors in a file.  I then ran the utility from the disk and it told me it was missing one file.  Then I learned about md5sum, so I downloaded again from a different machine.  I used md5sum and the hashes were equal.  I then burned to disc using, I think it's called "irarecorder" or something like that.  I did a check on the disk from the utility on it and it came up with errors in a file again.  Naturally, this frustrated the heck out of me.  I tried to install it anyway and it got to about 60% before I had to step away.  When I got back hours later the machine had gone to sleep.  When I woke it up it was frozen at 90%.  Does anybody know if this likely to install completely if I fix the Bios so that it won't go into sleep mode?  Can anybody explain whythe iso passes md5sum but the disk fails the self-test?  If this doesn't work what else can I do besides ordering a disk to be mailed to the house?

---

### Post by Kevbert on 2008-05-12
md5 hashes can be found here: [https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by Kevbert on 2008-05-12
If your iso file passes the checksum but fails the self test, it's normally due to errors during CD/DVD burning.  In the case of burning Hardy try setting the burn speed to the lowest possible (e.g. 2x instead of 32x).  If this fails you'll need to order a CD from [https://shipit.ubuntu.com/]("https://shipit.ubuntu.com/")

---

### Post by childofGod on 2008-05-12
Thanks,

Fortunately it worked on the second attempt and I'm using that computer with Hardy Heron right now.  I got rid of Microsoft and look forward to learning Ubuntu Linux.

---

