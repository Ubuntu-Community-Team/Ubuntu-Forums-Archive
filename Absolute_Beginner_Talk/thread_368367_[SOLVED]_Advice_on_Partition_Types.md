---
title: "[SOLVED] Advice on Partition Types"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by WorldTripping on 2007-02-23
Afternoon.

This weekend I'm going to install ubuntu. (Up until now I've been booting off the CD).

I have every intention of abandoning Windows completely.

However I do have historical Windows data; spreadsheets, document and the like.

I intend to store my data in on an external HDD.

So, the question is, which filesystem to use.

Obviously, the Ubuntu laptop will be ext3.

But what should I do with the external HDD.

Keep it as NTFS, and install the Linux ntfs-3g reader ?

If I format it as Fat32, will Ubuntu use it like that without installing anything else?

If I format it as ext3, wil my legacy data sit happily on it ? (I have a sneaking suspicion that this is the correct answer).

Thanks in advance.

---

### Post by george29 on 2007-02-23
ext3 or FAT32... as they both require the least amount of faffing to get working - they just work 'out of the box' unlike ntfs-3g.

if you are ever likely to plug the external hdd with your legacy data into another windows box then go with FAT32 - otherwise the alternative windows box will need to have drivers installed to allow it to read Ext3

george

---

### Post by WorldTripping on 2007-02-23
Hi Geoge29, and thanks for the reply.

Funnily enough, I was just looking at the drivers to enable a win box to read an ext3 partition.

Guess that I just needed some reassurance that Ubuntu would read/write onto a FAT32 drive OK.

So..It would be cool to have a totally Ubuntu laptop, with a FAT32 external HDD, and it will all work 'out-of-the-box' ??

(The possibility of plugging the drive into another Win box, but being able to use it with a Ubuntu machine, is one that I like..)

Cheers.

---

### Post by george29 on 2007-02-23
> **WorldTripping said:**
> Hi Geoge29, and thanks for the reply.

Funnily enough, I was just looking at the drivers to enable a win box to read an ext3 partition.

Guess that I just needed some reassurance that Ubuntu would read/write onto a FAT32 drive OK.

So..It would be cool to have a totally Ubuntu laptop, with a FAT32 external HDD, and it will all work 'out-of-the-box' ??

(The possibility of plugging the drive into another Win box, but being able to use it with a Ubuntu machine, is one that I like..)

Cheers.

Completely, that is what i have... 2 external hdd of 320 and 250Gb with FAT32 file system using a USB connection  - they automount and i can read and write to them... share them with my XP laptop, my debian etch laptop, XP or Ubuntu desktops. I just unmount and plug them into whichever machine i want - absolutely no faffing or worrying about drivers etc.

as far as i can remember i just plugged them in and they just worked - with no problems at all. 

george

---

### Post by WorldTripping on 2007-02-23
George29.

Thanks for that.

That is exactly the sort of setup that I'm looking at ending up with.

An Ubuntu laptop, running a LAMP server, for php and sql web development.

An old XP laptop running IIS, for asp development.

And an old tower set up as an Ubuntu Server, so I can share the external HDD's.

Thanks for your time.

---

