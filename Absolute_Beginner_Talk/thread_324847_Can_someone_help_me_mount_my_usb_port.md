---
title: "Can someone help me mount my usb port"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by calebjohnson77 on 2006-12-24
I have a 1.1 USB port.  I am trying to mount it so that I can transfer music files to my iriver t-30 mp3 player.

I just switched from Windows a few days ago, so I don't really understand the technical language.  A lot of the forums are saying that Ubuntu will automatically recognize it, but that isn't happening.

If it helps, I have the hoary hedgehog release, and am running gnome 2

Thanks,

Caleb

---

### Post by MkfIbK7a on 2006-12-24
does anything happen when you plug it in?

---

### Post by taurus on 2006-12-24
Plug it in, the open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here!

```
dmesg | tail
```

---

### Post by calebjohnson77 on 2006-12-24
First, thank you for your help.

When I did what you said, I got this response, but I still don't know how to pull up the window:

caleb@ubuntu:~$ dmesg | tail
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
hdc: irq timeout: status=0xd0 { Busy }
hdc: irq timeout: error=0x00
hdc: ATAPI reset complete
cdrom: dropping to single frame dma
usb 2-1: new full speed USB device using uhci_hcd and address 2
usb 2-1: USB disconnect, address 2
usb 2-2: new full speed USB device using uhci_hcd and address 3
usb 2-2: USB disconnect, address 3
usb 3-1: new full speed USB device using uhci_hcd and address 2
caleb@ubuntu:~$

---

### Post by calebjohnson77 on 2006-12-24
I think the USB is mounted.  I have a USB viewer that is now recognizing the mp3 player.  Someone said that I could just send the programs to the usb device by using the nautilus send to.  But that program is only giving me the option of sending emails with the Evolution email program.  Is there a way to add your usb device to the "send to" command?

Thanks,

Caleb

---

### Post by taurus on 2006-12-24
Just drag 'n drop like you would do in Windows!!!  However, you could run into permission so better start nautilus from a terminal with the sudo...

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

