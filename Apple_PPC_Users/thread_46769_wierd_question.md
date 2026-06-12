---
title: "wierd question"
date: 2005-07-06
forum: Apple PPC Users
---

### Post by leverknight1 on 2005-07-06
can i install 5.04 on a mac then install a pc pci video card and use it as my main video support

---

### Post by Len on 2005-07-06
Short answer: No. Unless you flash the card with a mac ROM which is rather hard.

Long answer: IBM PC cards doesn't work in the Macs. This is due to the different way of communication between the board (firmware) and the card, not due to Mac OS X.
The video cards have a piece of software that communicate with the chips onboard. This is called the firmware, bios, or whatever, and is stored in a ROM chip. The ROM chip can be modified. Since most ATI and NVidia cards don't differ much from the Mac versions except the firmware it is sometimes possible to "flash" (read: erase the PC firmware from the ROM and load a Mac firmware into it) the card and use it in the Mac.

If you happen to have accidently bought such a PC card, you should check these boards:
[http://strangedogs.proboards40.com/](http://strangedogs.proboards40.com/)

Note that you often have to solder or tape a connector to make the card work.

If you got such a card working on the Mac it will probably function with Linux as well.

---

### Post by leverknight1 on 2005-07-06
[QUOTE=Len]Short answer: No. Unless you flash the card with a mac ROM which is rather hard.

Long answer: IBM PC cards doesn't work in the Macs. This is due to the different way of communication between the board (firmware) and the card, not due to Mac OS X.
The video cards have a piece of software that communicate with the chips onboard. This is called the firmware, bios, or whatever, and is stored in a ROM chip. The ROM chip can be modified. Since most ATI and NVidia cards don't differ much from the Mac versions except the firmware it is sometimes possible to "flash" (read: erase the PC firmware from the ROM and load a Mac firmware into it) the card and use it in the Mac.

If you happen to have accidently bought such a PC card, you should check these boards:
[http://strangedogs.proboards40.com/](http://strangedogs.proboards40.com/)

Note that you often have to solder or tape a connector to make the card work.

If you got such a card working on the Mac it will probably function with Linux as well.[/QUOTE]
 oh ok thanks lots very informing

---

