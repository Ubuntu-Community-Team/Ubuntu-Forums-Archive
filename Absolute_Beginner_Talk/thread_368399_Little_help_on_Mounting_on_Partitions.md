---
title: "Little help on Mounting on Partitions"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Dannybzr on 2007-02-23
Hello all,

I have found my experience of the Ubuntu forums a brilliant source of help so far in my quest into the world of Ubuntu and Linux.

I'm still having a bit of trouble with regard to the install. Let me explain.

One 80GB HD in my pc, I have used partion magic in windows to create two partitions on my HD, These are an ext3 partition of 7GB in size and a Linux swap file that is 500mb in size.

Now I have run the Ubuntu live cd, version 6.10 and have run the installer. I have reached the point on the installer where it is asking me about mount points. this is where I am at a loss.

The screen gives the following details

**Mount Point**         Size                  **Partition **         Reformat

**/media/hda1**      67GB               **Primary hda1**           no

**/media/hda2**       7GB               ** Primary hda2 **          no

**swap **                 502MB             **Primary hda3**          yes

Now the first one (hda1) is the NTFS partition with windows on it
The secound is the ext3 partition, the third the swap.

Now I am at a loss here, I dont want to affect my windows partition in any way and I also want the option to choice which operating system to boot on startup.

Help is again much appreciated.......

---

### Post by Kateikyoushi on 2007-02-23
This guide might help you with the installation. [LINK]("http://www.psychocats.net/ubuntu/installing")

Your setting are fine, you might want to format hda2 as well not necessary if you did from partition magic. Your windows partition won't be formatted and will be in the grub menu aftr you finish install.

---

### Post by Dannybzr on 2007-02-23
Should I have logical partitions or should they all be primary??

Anyone care to shed any more light on this one for me

---

