---
title: "Boot modified SnowLeopard install with Grub2."
date: 2010-02-14
forum: Apple Hardware Users
---

### Post by kio_http on 2010-02-14
I modified SnowLeopard to install on mbr disk format. How can I chainload to the bootloader on the OS X partition using GRUB2. The autodetected entry MAC OS X put in by ubiquity on installing ubuntu doesn't work.

In grub legacy I just added an entry with root() and chainload and it worked.

How can I achieve this with grub2?

The computer is an Intel Mac.

I would readily use GUID, however I am unable to install Windows 7 on a GUID disk (without using bootcamp).

---

### Post by kio_http on 2010-02-19
BUMP!(Its been quite a long time)

___________________________________________________________________
There are certain support threads that tend to get no answers. The reason I post them is that I have no clue and its quite frustrating to know that others have no idea either. 
Unanswered posts team? Anyone?

---

### Post by kio_http on 2010-02-22
BUMP!! Again(Its been an even longer time, and not being able to boot an OS is a real problem)

---

### Post by tom4everitt on 2010-02-22
I know several people has had trouble with the default OS X entry. 

This worked for me:

```

menuentry "MacOSX" {
  insmod hfsplus
  # Search the root device for Mac OS X's loader.
  search --set /usr/standalone/i386/boot.efi
  # Load the loader.
  chainloader /usr/standalone/i386/boot.efi
}

```

Alternatively, you can skip the search and do it manually:


```

menuentry "MacOSX" {
  insmod hfsplus
  # Set the root device for Mac OS X's loader.
  set root=(hd0,2)
  # Load the loader.
  chainloader /usr/standalone/i386/boot.efi
}

```

If you've installed to any other place you will of course have to change the partition numbers.

Good luck

EDIT: Oh, if your computer is 64-bit (i.e core 2 duo), you might have to change the i386 part of /usr/standalone/i386/boot.efi. Check your OS X file system for what it should read instead.

---

