---
title: "[SOLVED] Software Raid (mdadm) Question"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-01-15
Can you go from 1 drive (NON-RAID) to a 3+ drive (RAID 5) array, even if the drive has data on it?
Basically, can you setup an array using a drive that already has data?

You see I am building a new rig and here are the spec's:
***_Case:**_ [Antec P182]("http://shop3.outpost.com/product/5178456")
***_PSU:**_ [Antec EA500]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817371007")
**_MoBo:**_ [Abit IP35-Pro]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813127030")
**_CPU:**_ [Q6600]("http://www.newegg.com/product/product.asp?item=N82E16819115017") (OC'ed to 3ghz w/ [Thermalright Ultra-120]("http://www.newegg.com/product/product.asp?item=N82E16835109125"))
**_RAM:**_ 2x [G.SKILL 4GB(2 x 2GB) DDR2 800 (PC2 6400)]("http://www.newegg.com/product/product.asp?item=N82E16820231122") [8GB total]
**_Vid Card:**_ el cheapo: [Asus EN8500GT]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814121094") - I won't be gaming so I don't need top-o-the-line
**_OS HD:**_ [WD Raptor 150GB]("http://www.newegg.com/product/product.asp?item=N82E16822136012")
**_Storage HD's:**_ 4x [WD Caviar SE16 750GB]("http://www.newegg.com/product/product.asp?item=N82E16822136131") (RAID 5) [2.25TB Total]
**_Optical Drive:**_ [Asus DRW-2014L1T]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827135156")
*[SIZE="1"]* - denotes already purchased[/SIZE]*
*[SIZE="1"]This build will be used as a workstation, and won't be used for gaming.[/SIZE]*

All together it's over $1500 with other misc expenses (artic silver, extra case fans, etc...), and I don't have $1500 right now, so I'll probably grow into this, meaning, I will only purchase 1 of the 4GB ram kits to start, and I'll only buy 1 of the 750GB HD's.  But If I start using that WD 750GB HD, can I later buy 3+ more and RAID it? or because it will have Data on it, NO?

TIA,
-BassKozz

---

### Post by dgray_from_dc on 2008-01-16
Yes and no, you can set up the array with three of the drives, transfer the data to the three drive array, and then add the fourth drive to the array.

Here is a guide [http://ubuntuforums.org/showthread.php?t=517282&highlight=mdadm+grow](http://ubuntuforums.org/showthread.php?t=517282&highlight=mdadm+grow)

---

### Post by BassKozz on 2008-01-16
So the main answer to my question is, NO you cannot create an array using a disk that already contains data... correct?

---

### Post by dgray_from_dc on 2008-01-17
Correct.

---

### Post by BassKozz on 2008-01-17
> **dgray_from_dc said:**
> Correct.

Thanks :)

---

