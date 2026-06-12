---
title: "Case in filenames - Linux / Windows"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by e_james on 2006-06-27
Can anyone explain why Linux (a case sensitive OS) insists on converting my upper case Windows file names to lower case and whether there is any way to stop this action?

---

### Post by stupidkid on 2006-06-27
I think this is something with the filesystem. I tried to create a folder (in Linux) on my FAT32 drive called "USAMTS" but it just became "usamts". When I do this on my ext3 drive, it worked fine.

---

### Post by Dr. Nick on 2006-06-27
I know some of it is filesystems, fat32 can be especially picky about weird symbols while most linux filesystems could care less what case/characters you use.

---

### Post by e_james on 2006-06-27
I found this explanation in wikipedia.

> If a filename contains only lowercase letters, or is a combination of a lowercase basename with an uppercase extension, or vice-versa, has no special characters, and fits within the 8.3 limits, a VFAT entry is not created on Windows NT. Instead, undocumented bits in byte 0x0c of the directory entry are used to indicate that the filename should be considered as entirely or partially lowercase. Specifically, bit 4 means lowercase extension and bit 3 lowercase basename, which allows for combinations such as "example.TXT" or "HELLO.txt" but not "Mixed.txt". Few other operating systems support this. Non-NT Windows versions see all-uppercase filenames if this extension has been used. By **default**, recent versions of Linux will recognize this extension but won't use it when writing.

So now I know why it's happening. I have highlighted the word "default". The implication is that default behaviour can be changed. I suspect this means a kernel recompile.

EDIT
My apologies to the Ubuntu developers and / or the latest kernel. They saw me coming. I have now tested Gedit and Nautilus. Upper case is preserved. I was testing Avidemux in Dyne:bolic (1.4.1) earlier today and it changed the case. Suse 9.3 also did it a few months ago. I just thought it was standard Linux behaviour.

---

