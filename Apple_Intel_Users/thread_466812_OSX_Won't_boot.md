---
title: "OSX Won't boot"
date: 2007-06-07
forum: Apple Intel Users
---

### Post by RobinTibbs on 2007-06-07
I have recently installed Ubuntu 7.04 on my first generation MacBook but have run into a problem.

Partitioning went fine, install went fine (i used the guide at [https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook)) and Ubuntu runs like a dream, however on the Mac OSX boot menu, I can only select my Ubuntu partition. I conceed that I may have done something wrong, but I am not sure what.

I can mount my Mac partion fine in Ubuntu so I haven't hosed it completely so I'm guessing it's a bootloader related issue.

Many thanks in advance

---

### Post by Gen2ly on 2007-06-07
This is just possibly rEFIt, try installing it from a CD, there's directions on the website.  If you installed from the wiki, I'd think your partitioning is safe.  If you try "fdisk -l" does it show something like this:

```
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26        2898    23068672   af  Unknown
/dev/sda3   *        2914        6047    25165824   83  Linux
/dev/sda4            6047        9730    29580336   83  Linux
```

fdisk will show the OS X (/dev/sda2) as Unknown because it doesn't recognize HFSplus, but you will at least see if you didn't accidentally erase it.  Peace out.

---

