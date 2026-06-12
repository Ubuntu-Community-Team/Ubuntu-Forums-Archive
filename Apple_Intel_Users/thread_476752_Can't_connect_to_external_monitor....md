---
title: "Can't connect to external monitor..."
date: 2007-06-17
forum: Apple Intel Users
---

### Post by Torajima on 2007-06-17
I can't connect my Macbook to an external monitor (1280 x 720 DLP).

I get an error saying the X server has shut down (or something similar).

Here's the final  bit from my Xorg log:

> (EE) I810(0): No Video BIOS modes for chosen depth.

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x6d) [0x48282d]
1: /lib/libc.so.6 [0x2b275149ad40]
2: /usr/lib/xorg/modules/drivers//i810_drv.so [0x2b27536261b2]
3: /usr/lib/xorg/modules/drivers//i810_drv.so [0x2b275362a7b8]
4: /usr/X11R6/bin/X(InitOutput+0x9bc) [0x4657ec]
5: /usr/X11R6/bin/X(main+0x275) [0x436e55]
6: /lib/libc.so.6(__libc_start_main+0xf4) [0x2b27514878e4]
7: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x241) [0x436339]

Fatal server error:
Caught signal 11.  Server aborting

Oh, and I'm connecting via VGA.

---

### Post by Torajima on 2007-06-19
Bump...

---

