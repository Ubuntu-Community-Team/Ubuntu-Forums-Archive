---
title: "Boot error messages: what are they telling me?"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by nietorigineel on 2006-10-16
```

[17179593.144000] Bluetooth: HCI USB driver ver 2.9
[17179593.144000] usbcore: registered new driver hci_usb
[17179593.300000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179593.300000] Floppy drive(s): fd0 is 1.44M
[17179593.324000] FDC 0 is a post-1991 82077
[17179593.632000] codec_read: codec 0 is not valid [0xfe0000]
[17179593.636000] codec_read: codec 0 is not valid [0xfe0000]
[17179593.644000] codec_read: codec 0 is not valid [0xfe0000]
[17179593.652000] codec_read: codec 0 is not valid [0xfe0000]
[17179594.020000] lp0: using parport0 (interrupt-driven).
[17179594.128000] Adding 409616k swap on /dev/hda7.  Priority:-1 extents:1 across:409616k
[17179594.200000] EXT3 FS on hda3, internal journal

```

This is part of dmesg. Didn't want to post the entire thing, since i'm not sure if that is needed. 

So how do i find out what is not going as it should here, and how to repair?

[edit]

Might be wise to tell something about my install:

Xubuntu server install,

after that put on the xfce DE on myself (not xubuntu-desktop)

---

### Post by nietorigineel on 2006-10-17
*bump*

---

### Post by petri on 2006-10-17
It seems like the codecs you apparently have installed aren't working. Codecs decodes the mp3 and DVD movie files if I have got it right.

---

### Post by nietorigineel on 2006-10-18
I don't remember installing codecs, but I'll look into that. Could they have come with VLC/XMMS? (In Windows, VLC doesn't need any codecs installed, so that would leave XMMS as the most probable candidate)

Is there a way to FIND what the error message is pointing to? (e.g. by the number that is posted before it, it can't be there without reason) Or at least the actual boot command that caused it, so i can see where that is pointing to.

---

### Post by petri on 2006-10-18
What error messages do you get? 
Does your mediaplayers work?

---

### Post by nietorigineel on 2006-10-18
xmms and vlc both work (at least on all the files i tried)

the error message at boot was posted in the first post, but i left some stuff around it there (thought that providing a context might be helpful to localize it).

anyway the actual error part:

```

[17179593.632000] codec_read: codec 0 is not valid [0xfe0000]
[17179593.636000] codec_read: codec 0 is not valid [0xfe0000]
[17179593.644000] codec_read: codec 0 is not valid [0xfe0000]
[17179593.652000] codec_read: codec 0 is not valid [0xfe0000]

```

---

