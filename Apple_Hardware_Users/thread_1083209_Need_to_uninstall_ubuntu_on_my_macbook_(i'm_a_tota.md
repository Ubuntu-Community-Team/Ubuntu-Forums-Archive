---
title: "Need to uninstall ubuntu on my macbook (i'm a total newbie to linux)"
date: 2009-02-28
forum: Apple Hardware Users
---

### Post by spiper09 on 2009-02-28
I need to uninstall linux/ubuntu on my macbook tiger (i still havent upgraded it yet). I partitioned my hard drive, and installed linux on the new portion of my hard drive. (if that made any sense). I don't have the original CD that came with it because a friend lent it to me to install. I'm lost. Help? Thanks :confused:

---

### Post by cybergalvez on 2009-02-28
> **spiper09 said:**
> I need to uninstall linux/ubuntu on my macbook tiger (i still havent upgraded it yet). I partitioned my hard drive, and installed linux on the new portion of my hard drive. (if that made any sense). I don't have the original CD that came with it because a friend lent it to me to install. I'm lost. Help? Thanks :confused:

Not sure what your question is? I'm assuming by original CD you mean the original Mac cd, something should have come with your macbook.  What do you need help with?

---

### Post by McFrostey on 2009-02-28
> **cybergalvez said:**
> Not sure what your question is? I'm assuming by original CD you mean the original Mac cd, something should have come with your macbook.  What do you need help with?
im pretty sure he wants all OSX back and no Linux on his HD
i dont know the answer but i do know the question ;)

---

### Post by cyberdork33 on 2009-02-28
Boot from an Ubuntu Desktop CD. You can download and burn one from ubuntu.com

Once Booted, run the partition editor from the System > Administration menu.

you can use this tool to delete the Ubuntu partition and it's swap partition (you should have a EFI partition and the HFS+ partition left). done.

You will still need to boot back into OSX and figure out how to resize your partition to fill the free space, or use disk utility to create a new partition in the free space.

---

