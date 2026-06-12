---
title: "Ubuntu on White Macbook 2,1"
date: 2017-01-27
forum: Apple Hardware Users
---

### Post by hallissyc on 2017-01-27
Good Evening, 

I have an old mid-2006 white macbook 2,1 and I have been experimenting putting Ubuntu on the last few weeks but am hitting some snags. I am using a usb with the boot/efi folders with .iso files and the efi boot file. I boot holding alt and choose the efi boot option and can launch a live session of ubuntu (or any 32 bit distro). I can install the distro, but when I restart the mac it doesn't boot back up with Ubuntu. I just get a black screen with a white blinking cursor. What am I doing wrong?

---

### Post by &amp;KyT$0P# on 2017-01-27
Did you install [rEFInd]("http://www.rodsbooks.com/refind/") on your Mac?

---

### Post by hallissyc on 2017-01-28
No, as I didn't intend on dual booting. I followed a thread that instructs how to efi boot the old 2,1's. I boot just fine off of the .iso on the live usb, run the sudo gparted command, delete all partitions, install the distribution, and then restart using an old snow leopard dvd I have. I open up terminal and try to bless the new install so that it will boot off of the linux partition and I am stuck. Any suggestions?

---

### Post by g33zr on 2017-01-28
I assume you created an efi boot partition, but did you also select the esp flag for that partition?

---

### Post by kcunak on 2017-02-07
Ubuntu 16.04 LTS
=====
I have read many threads and have been trying for weeks off and on to get my white macbook 2,1 to boot from the internal hard drive to no avail.  I have no issues booting from a USB key; however, the last leg to having the macbook boot all on its on, I am totally stumped.   I have followed numerous guides that I have found on the internet but inevitably after executing numerous steps in terminal I hit a brick wall and start getting the dreaded error messages.  The walk-throughs seem so simple but there is always a snag somewhere.  This 32-bit EFI autonomous boot issue is really taking me for a ride.

I am posting my boot-repair print out that can be found here:  [http://paste2.org/j8xJ0xCX](http://paste2.org/j8xJ0xCX)

Any insight and clear and simple direction (for a novice) on how I can get Ubuntu up and running on a Macbook 2,1 32-bit EFI system without the need to boot from a USB key would greatly be appreciated.  In the meantime, I will persevere and keep searching.

---

### Post by kcunak on 2017-02-07
> **halogen2 said:**
> Did you install [rEFInd]("http://www.rodsbooks.com/refind/") on your Mac?

On my USB key I created another folder (refind-flashdrive-0.10.4) at the same level as my EFI folder and Ubuntu USB key automatically boots when inserted.  No need to press any keys on the keyboard.  It just boots right up into Ubuntu after about 30 secs or so.

See the attached image for my USB folders setup.

---

