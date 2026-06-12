---
title: "my computer does not load"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by am_rods on 2007-03-21
when i turn my computer on it starts loading ubuntu, but when the loading bar fills my display stays blank. i have to turn my computer off manually (pressing the on/off button for several seconds), and then i turn it on again and it starts ubuntu normally. i have to do this procedure every time i want to use my computer and i am afraid it might damage my hardware. i have a thinkpad t22 with 900 processor and 512 ram.

---

### Post by rennen01 on 2007-03-21
When you see the Ubuntu Loading Bar, press either ALT+F1 or CTRL+F1.

This will give you the text of what is loading.  Post what is locks up on here.

---

### Post by am_rods on 2007-03-21
what appears is:

Booting 'Ubuntu, kernel 2.6.17-11-386'

root    (hd0.1)
 Filesystem type is ext2fs, partition type 0x83
kernel    /boot/vmlinuz-2.6.17-11-386 root=UUID=2db50014-1448-4221-be20-6a117cc0b
414 ro quiet splash vga=normal
      [Linux-bzImage, setup=0x1c00, size=0x17e746]
initrd   /boot/initrd.img-2.6.17-11-386
      [Linux-initrd @ 0x1f946000, 0x689dc7 bytes]
savedefault
boot
[17179607.220000] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may
 corrupt your serial eeprom! Refusing to load module!
 * Activating swap...                                                                                        [ ok ]
 * Checking root file sytem...
fsck 1.39 (29-May-2006)
/dev/hda2: clean, 105900/393600 files, 726480/787185 blocks
                                                                                                             [ ok ]
* Checking file systems...
fsck 1.39 (29-May-2006)
                                                                                                             [ ok ]

Ubuntu 6.10 protoss tty1

protoss login: _


after that the displays stays blank

when i turn it on again it displays this:

Booting 'Ubuntu, kernel 2.6.17-11-386'

root    (hd0.1)
 Filesystem type is ext2fs, partition type 0x83
kernel    /boot/vmlinuz-2.6.17-11-386 root=UUID=2db50014-1448-4221-be20-6a117cc0b
414 ro quiet splash vga=normal
      [Linux-bzImage, setup=0x1c00, size=0x17e746]
initrd   /boot/initrd.img-2.6.17-11-386
      [Linux-initrd @ 0x1f946000, 0x689dc7 bytes]
savedefault
boot
[17179603.036000] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may
 corrupt your serial eeprom! Refusing to load module!
 * Activating swap...                                                                                        [ ok ]
 * Checking root file sytem...
fsck 1.39 (29-May-2006)
/dev/hda2: clean, 105893/393600 files, 726493/787185 blocks
                                                                                                             [ ok ]
* Checking file systems...
fsck 1.39 (29-May-2006)
                                                                                                             [ ok ]

Ubuntu 6.10 protoss tty1

protoss login: _


and then it loads fine

---

### Post by drseuk on 2007-04-04
Confirmed. The same problem began recently (March / April 2007) on my Thinkpad T20 which was booting fine before.

Anyone got a fix?

---

