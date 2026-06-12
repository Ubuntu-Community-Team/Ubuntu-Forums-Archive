---
title: "Backlight Isssue"
date: 2007-05-06
forum: Apple Intel Users
---

### Post by The_Giver on 2007-05-06
I get this problem:


[https://launchpad.net/ubuntu/+source/pciutils/+bug/87436/+viewstatus](https://launchpad.net/ubuntu/+source/pciutils/+bug/87436/+viewstatus)

-- snip ---
mgalvin@bender:~/Projects/macbook-backlight$ make
gcc -Wall -g -Wextra -DVERSION=\"0.1.1\" backlight.c -o backlight -lpci
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libpci.a(names.o): In function `pci_load_name_list':
(.text+0x538): undefined reference to `gzopen'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libpci.a(names.o): In function `pci_load_name_list':
(.text+0x5d1): undefined reference to `gzgets'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libpci.a(names.o): In function `.L154':
(.text+0x6d6): undefined reference to `gzclose'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libpci.a(names.o): In function `.L154':
(.text+0x6f8): undefined reference to `gzeof'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libpci.a(names.o): In function `.L154':
(.text+0x795): undefined reference to `gzclose'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libpci.a(names.o): In function `.L154':
(.text+0xbdb): undefined reference to `gzopen'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libpci.a(names.o): In function `.L157':
(.text+0xd78): undefined reference to `gzerror'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libpci.a(names.o): In function `.L157':
(.text+0xd9b): undefined reference to `gzclose'
collect2: ld returned 1 exit status
make: *** [backlight] Error 1
--- snip ---

after following this: 

[http://ubuntuforums.org/showthread.php?t=434528](http://ubuntuforums.org/showthread.php?t=434528)

---

### Post by Chrisj303 on 2007-05-06
When you installed Feisty, you did select the apple mac option when prompted to pick a keyboard type didn't you?

If so then the backlight keys on your keyboard should work out of the box.

This was an issue in edgy, but not now with feisty.

If you didn't select Mac on the keyboard select screen, try doing it from within ubuntu

SYSTEM. > PREFERENCES > KEYBOARD

---

### Post by Tyrdium on 2007-05-06
I guess that line isn't for 64-bit users only, then. Thanks for testing it for me.

Try: gedit Makefile, change *gcc $(CFLAGS) $^ -o $@ $(LIBS)* to *gcc $(CFLAGS) $^ -o $@ $(LIBS) -lz*

---

### Post by The_Giver on 2007-05-06
Even after chaning that I'm still having issues.. maybe it has to do with that gzopen gzclose stuff?

---

