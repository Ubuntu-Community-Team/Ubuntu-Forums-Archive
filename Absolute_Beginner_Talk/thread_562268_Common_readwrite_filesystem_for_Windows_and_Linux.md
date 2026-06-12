---
title: "Common read/write filesystem for Windows and Linux"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by T3KN33K on 2007-09-28
Hello.  As I have stated in previous posts, I am relatively new to Ubuntu, and Linux in general.  I have a 500GB external USB hard drive that I use to store media on (ie music, movies, software installers, etc.).  This HDD came formatted in FAT32 filesystem, which, in my very limited understanding, is much less capable than NTFS at large partition sizes.  Exactly what this entails, I'm not sure.  That said, I recently accidentally formatted the hard drive, and I have not yet chosen a new filesystem.  This gives me the opportunity to find out exactly what my options are.

Basically, the ideal for me would be to be able to both read and write to the external HDD from both Vista and Feisty.  Any suggestions on how I would best go about achieving this would be appreciated.

---

### Post by hotweiss on 2007-09-28
Well the only one that will read and write out of the box in both systems is FAT32 as far as I know. Although you can configure Ubuntu to write on an NTFS drive and you can configure Vista to write on a ext3 drive, etc...

---

### Post by rsambuca on 2007-09-28
I think the best choice is ext3, since it is a little better filesystem than ntfs.  You can then install the [fs-driver]("http://www.fs-driver.org/") in Vista (use the XP compatibility mode when installing) so that you can read and write from both OS's

---

### Post by CaptainInsaneO on 2007-09-28
I agree with what they said.

---

### Post by T3KN33K on 2007-09-28
um..  not sure how else to ask this...  but what would the degree of "messiness" be with going with an ext3 filesystem?  as in, how much extra clutter or disorganization would each os leave on the drive, if any?

---

### Post by CaptainInsaneO on 2007-09-28
NTFS fragments more than ext3, here's how they work:

When receiving new data, NTFS finds any open area on the disc to dump it, and then links the data together into one file in the file table of the disc.

ext3 works a little the same way, except it searches for the first contiguous free space it can find for a file, instead of throwing bits all over Hell's half acre. This results in less file fragmentation, because most (or all) of the file's pieces are physically right next to each other.

---

