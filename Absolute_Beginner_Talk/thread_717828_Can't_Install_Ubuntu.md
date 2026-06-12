---
title: "Can't Install Ubuntu"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by bsmash on 2008-03-07
Hi,

I download the ubuntu 7.10 iso, and burn it. When I boot from the CD, the startup menu apears, but when i choose a option, nothing happens.

The only option that works is to boot from the harddisk.

I already have downloaded the iso twice and the same happens.

some help?

Bruno

---

### Post by taurus on 2008-03-07
How fast did you burn it to a CD?  Did you pick the Scan disc for defects option on the first menu to make sure the CD is good?

What's the spec of your machine?

---

### Post by bsmash on 2008-03-07
I did not verify if the cd is good. But i tried to install in a virtual machine too, and boot directly from de iso imagem and happens the same.

I have a AMD X2 4200+, with 2Gb of ram 800MHz, a Nvidia 8800 GTS.

---

### Post by Fixman on 2008-03-07
Try to choose the  "check CD for defects" option.

---

### Post by stchman on 2008-03-07
> **bsmash said:**
> Hi,

I download the ubuntu 7.10 iso, and burn it. When I boot from the CD, the startup menu apears, but when i choose a option, nothing happens.

The only option that works is to boot from the harddisk.

I already have downloaded the iso twice and the same happens.

some help?

Bruno

Try the alternate install CD.

---

### Post by mikewhatever on 2008-03-07
> **bsmash said:**
> Hi,

I download the ubuntu 7.10 iso, and burn it. When I boot from the CD, the startup menu apears, but when i choose a option, nothing happens.

The only option that works is to boot from the harddisk.

I already have downloaded the iso twice and the same happens.

some help?

Bruno

You may download that iso 20 times with the same result. What you need to do, is to md5sum check it or use bittorrent. [https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29](https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29)

---

### Post by bsmash on 2008-03-07
I already have tried. Only one of the options works and it is the "BOOT from the first hard Disk"

I have tried in another PC and happens exaclty the same.

---

### Post by bsmash on 2008-03-07
I've used the Md5Sum to check and they are diferent. Why this happens?

what do i have to do?

thaks to all

Bruno

---

### Post by mikewhatever on 2008-03-07
> **bsmash said:**
> I've used the Md5Sum to check and they are diferent. Why this happens?

what do i have to do?

thaks to all

Bruno

First, check the numbers you got with the correct one for your version [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/releases/7.10/MD5SUMS](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/releases/7.10/MD5SUMS). If one of yours match, that iso is good and the problem is elsewhere.
> ebf7ad055bc39634065daa10de980d7e *ubuntu-7.10-alternate-amd64.iso
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
43ff753b260729b12c7d21d3a6db8c73 *ubuntu-7.10-server-amd64.iso
7d88cd87df509a740d9f47b9bbf1375e *ubuntu-7.10-server-i386.iso
5308a79f5e652edba5be84644ee14b09 *ubuntu-7.10-server-sparc.iso

I always use a bittorrent client, utorrent, if you are on Windows for such downloads. Bittorrent checks every piece before writing to disk, so that you do not get any errors in the end.

---

### Post by bsmash on 2008-03-07
I already have checked the keys. I'will try the torrent client.

tks

---

