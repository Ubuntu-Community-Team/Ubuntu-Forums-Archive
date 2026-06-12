---
title: "Gnomad hangs"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by lunarmelody on 2007-04-16
I have gnomad installed, and it can read my mp3 player.  I scans all the songs in the library, but hangs when it tries to scan the playlists.  Is there any way to fix this, or change the settings so that it doesn't try to scan the playlist info?  Thanks!

---

### Post by speeves on 2007-04-16
Are you getting any errors when this happens?

thanks,

---

### Post by lunarmelody on 2007-04-16
No, no error messages.  It just does nothing.

---

### Post by lunarmelody on 2007-04-17
After playing around with it today, I had the same problem, but I got the following error message:

LIBNJB Panic: Unknown playlist frame 0000, length 0001 bytes
Segmentation fault (core dumped)

Anyone know what this means?

---

### Post by lunarmelody on 2007-05-01
Alrighty, updated to fiesty, removed then reinstalled gnomad2, then ran it from a terminal.  Here's the output:

This is not a Microsoft MTP descriptor...
Device response to read device property 0xee:
        0000: 7b06 5810 0109 0801 c032 00a0 602c c000   {.X......2..`,..
        0010: 0403 0904 2003 5700 6500 7300 7400 6500   .... .W.e.s.t.e.
        0020: 7200 6e00 2000 4400 6900 6700 6900 7400   r.n. .D.i.g.i.t.
        0030: 6100 6c00 1a03 4500 7800 7400 6500 7200   a.l...E.x.t.e.r.
        0040: 6e00 6100 6c00 2000 4800 4400 4400 0403   n.a.l. .H.D.D...
        0050: 3000 0000 0000 0000 0000 0000 0000 0000   0...............
        0060: 0000 0000 0000 0000 0000 0000 0000 0000   ................
        0070: 0000 0000 0000 0000 0000 00                         ...........
This is not a Microsoft MTP descriptor...
Device response to read device property 0xee:
        0000: 0079 4d46 473a 4850 3b4d 444c 3a44 6573   .yMFG:HP;MDL:Des
        0010: 6b6a 6574 2033 3834 303b 434d 443a 4c44   kjet 3840;CMD:LD
        0020: 4c2c 4459 4e3b 434c 533a 5052 494e 5445   L,DYN;CLS:PRINTE
        0030: 523b 4445 533a 3338 3435 3b53 4e3a 5448   R;DES:3845;SN:TH
        0040: 3535 4f31 3333 3557 3034 3052 3b53 3a30   55O1335W040R;S:0
        0050: 3338 3030 3038 3030 3030 3230 3032 3030   3800080000200200
        0060: 3332 6331 3465 3030 3030 6332 3530 3030   32c14e0000c25000
        0070: 3030 3b5a 3a30 3037 3b                                  00;Z:007;
No MTP devices.
This is a PDE device

Still the same problem:  gnomad loads the songs, then freezes.  Any ideas, or suggestions of another program to use?  Thanks!

---

