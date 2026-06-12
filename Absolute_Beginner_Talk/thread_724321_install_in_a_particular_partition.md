---
title: "install in a particular partition"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by paraglider on 2008-03-14
Please help a poor noob!!

OK, just downloaded ubuntu... checked that the cd works and now want to install it on my vaio vgnfz21s

I have previosly made a partition in windows (20GB) and have left it unformatted.

I´d like to install ubuntu onthat partition, but i´m not sure how.

Thanks in advance!

---

### Post by scragar on 2008-03-14
ubuntu will offer you the choice of where to install it, I'm sure one of the options is to overwrite an existing partition, choose that one.

---

### Post by sandysandy on 2008-03-14
have a look at these links for dual booting

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

also post full system specs including partitions.

regards

---

### Post by paraglider on 2008-03-14
ok, apparently it doesn´t let me choose a particular partition.

Options are:

Use whole disk

Shrink a formatted partition and use extra space

Custom install- however doesn´t let me shrink the unformated partition

I shrunk a diferent partition in vista by 1GB for SWAP, and will use my unformated partition as ext3 and lbel it /

Otherwise i´ll back up an existing nfts partition and tell it to "shrink and use exta space"

If i´m doing it all wrong someone please stop me!!
:popcorn:

---

### Post by scragar on 2008-03-14
use custom, delete the old partition and assign some free space for swap, with the rest formated ast ext3 and mount to /

---

### Post by sandysandy on 2008-03-14
> **paraglider said:**
> ok, apparently it doesn´t let me choose a particular partition.

Options are:


Custom install- however doesn´t let me shrink the unformated partition



If i´m doing it all wrong someone please stop me!!
:popcorn:

with gparted u can change the size of desired partition and format to ext3.

after that install Ubuntu.

regards

---

