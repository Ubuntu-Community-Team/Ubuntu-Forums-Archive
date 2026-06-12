---
title: "Need help install Ubuntu 6.10 - First time user"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Future Proof on 2007-03-29
I'm currently running WinXP Home on a Seagate 200Gb SATA HDD.
I recently downloaded Ubuntu from the official website and I put it onto a disc.
I'm not sure if this matters, but the CD Check found 3 checksum errors. :confused: 
Anyway...
I can get to the screen where the options are displayed, Run & Install, Check CD etc.
If I select Install......i wait for a bit.........and I get an error message saying that Server X failed to start.
I'm completely new to this sort of thing so I would like some easy-to-understand advice on how to successfully install it on the same hard drive as Windows.

I was thinking that I should get a program that enables me to edit partitions so I can select 50/50 or something like that - so Ubuntu can install; but this may not be causing the problem so i could be wrong.

Again, I'm an absolute beginner so any advice is appreciated
Thanks.

---

### Post by Obor on 2007-03-29
If your cd checksum shows error you need to burn the cd again or download it again if the file is corrupted.

[Here is]("http://www.psychocats.net/ubuntu/installing") a step by step guide to dual boot ubuntu with windows

And [here]("http://www.psychocats.net/ubuntu/iso") is a little guide to burning iso images etc.

---

### Post by PointSource on 2007-03-29
The three checksum errors are important, it shouldn't find any, and those errors in the CD may be what's causing your X server to not load. Perhaps you should try to download the Ubuntu CD again, or if you still have the ISO image verify it has the correct md5 sum

---

### Post by justleen on 2007-03-29
first off, the cd check should not give any errors.

So.. the failed X server start might be due to the checksum errors.

What you can try: when on the boot menu, press F4, and select a resolution and color depth that your video card supports... might help/.

---

### Post by Future Proof on 2007-03-29
Thanks for the replies!
I'll try burning it again and checking. What should I do if the md5 sum is incorrect?
Is it possilbe to somehow 'fix' the ISO (if that's the problem) instead of downloading it again?

Also, Will I have to make a new partition?

---

### Post by dptxp on 2007-03-29
If MD5 check fails download again.
iso images are burnt by Infra Recorder in Windows or at speeds not more than 4X by programs like NERO.

After you run the right Live+install CD, click install. In step 5 (I think step 5) you will get options to partition. You can keep 50/50. Ubuntu can access FAT32 partitions and EXT3, Windows can access EXT3 only with additional software in Windows.

Keep about 10-12 GB for 'root'  ('/'), 2 GB to 4 GB for 'SWAP', and rest as you like. Make sure that you do not format your Windows part (un-tick if ticked).

Spare drives/partitions can be formated in EXT3 or FAT32, EXT3 is better as per my interpretation. Windows shall read EXT3 with addl software in it as said earlier.

---

### Post by mpokrywka on 2007-03-29
If your iso is corrupt you don't have to download it all again - use torrent ([http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/)  e.g. [http://releases.ubuntu.com/6.10/ubuntu-6.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/6.10/ubuntu-6.10-desktop-i386.iso.torrent) ), and when bittorrent application asks you for directory where to download -> enter directory where your iso is.
Bittorrent app will check iso image and only download corrupt pieces.

---

### Post by dptxp on 2007-03-29
It is always advisable to download using Bittorrent.
I did not know that it corrects files too. Thanks for this info.

---

### Post by Future Proof on 2007-03-29
> **mpokrywka said:**
> If your iso is corrupt you don't have to download it all again - use torrent ([http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/)  e.g. [http://releases.ubuntu.com/6.10/ubuntu-6.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/6.10/ubuntu-6.10-desktop-i386.iso.torrent) ), and when bittorrent application asks you for directory where to download -> enter directory where your iso is.
Bittorrent app will check iso image and only download corrupt pieces.

I just did this and I was able to install everything OK!
Thanks very much for your help!

---

