---
title: "Flash Drive Questions"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by MikeEnIke on 2007-03-07
Alright I have two question that I assume will be simple fixes, i just can't quite figure out how, and searching through the forums blasts me with too many threads that i can't even begin to search through.

1) How do I name my flash drive? When formatting it in Windows (yea yea yea) you simple change the name, with gparted, I don't have the option?

2) Will windows machines recognize my dual partition flash drive? Or will it only recognize one of the partitions? I would like to have USB Edgy on one partition so i can spread ubuntu to everyone i know, but i also use my usb flash drive to fix other's computers and store my main programs on that which I use to do so, so I really want to have the ubuntu partition for spreading the word and the programs partition for making the bread :P

Thanks

---

### Post by kolinab on 2007-03-07
Regarding labelling your key - someone posted a good link for me a while ago:

[http://doc.gwos.org/index.php/Understanding_fstab#How_to_Label](http://doc.gwos.org/index.php/Understanding_fstab#How_to_Label)

If you make the programs partition FAT32 then Windows and Ubuntu will both see it. That's probably the safest way to go. I just made my key all FAT32, but then again I didn't install the OS to it (yet). From what I've read the reading and writing to a key from the OS can be a little hard on them. I still kind of want to try it.

K

---

### Post by MikeEnIke on 2007-03-07
Yea, i have a 5 year warranty, mide aswell take advantage of it :), i had both in fat, but my windows seems to only pick up one of the two partitions, one is fat16 (the ones it sees), and the other is fat32. Thanks for the link

---

