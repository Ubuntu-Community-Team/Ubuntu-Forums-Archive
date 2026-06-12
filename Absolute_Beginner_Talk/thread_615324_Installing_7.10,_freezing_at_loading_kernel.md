---
title: "Installing 7.10, freezing at loading kernel"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Marfish on 2007-11-16
This is my first experience with linux, and am having a hard time with this. I was under the impression this would be a smooth process, but got a little testy when I waited for the loading bar for about an hour, which didnt want to budge from 18%. Ive tried loading it numerous times, all stopping at 18%, and occasionaly 22%. This is all at the first loading process, "loading kernel". So I basicaly cant use any of the options listed on the main page. Ive tried some of the codes people were saying to use, like acpi=off, noapic, nolapic, and cpi=noacpi. Im not sure if this is supposed to be used with the codes in the special boot bar, or delete the other codes on there and add only these. I tried only adding and didnt try to delete what was there.

---

### Post by uclalinux on 2007-11-17
Make sure the CD is not corrupt, I would run a MD5 Check in widows, or just re-burn it, or re-download it from torrents, it takes like 10 min's. Also what hard where are  you running? If all else fails try Ubuntu 7.04.

---

### Post by Inxsible on 2007-11-17
> **uclalinux said:**
> Make sure the CD is not corrupt, I would run a MD5 Check in widows, or just re-burn it, or re-download it from torrents, it takes like 10 min's. Also what hard where are  you running? If all else fails try Ubuntu 7.04.
Also check the CD for errors by using the second option when you first boot up using the CD. Also what speed did you burn the iso at? recommended speeds are 4x or less

---

### Post by Marfish on 2007-11-17
Thank you both very much. I wiped the disk and burned it again at 4x, last time I burned it at 10x. Lol. I am actually in the middle of the installation right now, and am trying to get it onto an external hard drive. Im an too worried about wipping my internal hard drive and was hoping someone could help me along from where I am, and give me a heads up. right now I am choosing a partition, which I chose 92% of the hard drive which is 100.8 gigs. I then chose guided - resize SCSI8 (0
I now have a list of devices to choose from, one has winodws, one is a recovery, and the last is the external. Here is my list.

/dev/sda
/dev/sda2  fat32  /media/sda2  -   7345mb  3200mb
/dev/sda1  ntfs    /media/sda1  -   112678mb  51600mb
free space                                 -    8mb
/dev/sdb
/dev/sdb1                                  -    120031mb   33mb

I have nothing on the external hard drive except preinstalled software from the company. Is the bottom one the one I want to choose. Is there anything special I should do to make it work for the external hard drive. Thanks to anyone that answers my extremely noobish questions.

---

### Post by zabien1970 on 2007-11-17
Wiped the disk and burned it again?  You should be using a cd-r , cd-rw isn't recomended

---

