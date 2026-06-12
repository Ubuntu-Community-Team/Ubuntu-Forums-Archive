---
title: "an abstract question..."
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2006-05-27
i have a friend who asked me to format his hdd but he wants something like low level format (im not quite sure what's that but i've understood that's something like earsing all the data from hdd)....is this possible? :confused: :confused:

---

### Post by Koech on 2006-05-27
Your question is not so clear but I beleive you can format a hard disk quite easily to a file system of your choice ie NTFS/FAT using Windows install CD, extfs with a Linux CD and so forth. If you meant else, then I'm sorry, I don't know much about it.

---

### Post by skippy81 on 2006-05-27
Low level formats no longer exist, it was a mechanism by which the hard disk was 'formatted' in the BIOS to make it useable by an operating system.

Nowadays the term "low level format" is used to refer to zero-filling.  You zero fill a disk when you write the entire thing with binary "0".  This restores the disk to a 'factory' state, and makes it much harder to recover deleted files from it. No doubt the FBI could still fish out your old files though.  

The manufacturer of your drive will probably have a downloadable utility for zero-filling a drive - I know seagate do. 

You can search around for a windows or linux zero filling utility, or if your feeling brave use this little tip here:

WARNING :- THE TIP GIVEN IN THIS LINK IS NOT FOR BEGINNERS [http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill]("http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill")

Whatever you do, make sure you know which of your drives is which, the above tip will destroy the contents of whichever drive is /dev/hda/

Zero-filling wipes the ENTIRE DRIVE, including partitions and, I assume, the MBR.  So you really should understand what you are doing before you do it.

IMHO it is totally unnecesary to zero-fill a drive unless you have some seriously incriminating data on the drive, and even then I doubt zero-filling with guarantee your safety.  If your friend is using windows, then you can just download a little zero-filling program (search google for 'zero fill') and do it for him without having to remove the drive.  Afterwards the drive will be like new and can be formated as normal.

---

### Post by Koech on 2006-05-27
I got some more info for you, low level format means total erasure of data in a dik esp to get rid of viruses that may have gotten to boot sector or mbr. It is a risky thing to do but if you need to, just use manufacturer specific utilities. [This]("http://www.ariolic.com/activesmart/low-level-format.html") may be of help.

---

