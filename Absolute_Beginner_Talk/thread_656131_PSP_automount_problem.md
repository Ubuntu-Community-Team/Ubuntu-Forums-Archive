---
title: "PSP automount problem"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by T-Grave on 2008-01-02
Hi evryone, 

I'm new on the forums, but I've worked with ubuntu over a year by now.

I've installed a command-line 7.10 Gutsy on some old laptop of mine.
I've managed to automount my PSP but it only does this on startup when it's plugged in...
And it would be very handy if it automount everytime I plug it in, I've placed some outputs here, you never know it's because of them ...

When mounted on boot

lsusb command:
> 
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 054c:01c8 Sony Corp.
Bus 001 Device 001: ID 0000:0000


Second time:

lsusb command:
> 
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 054c:01c8 Sony Corp.
Bus 001 Device 001: ID 0000:0000


Another output I get when it's replugged:
> 
[734.536000] sd 3:0:0:0; [sdb] Assuming drive cache: write trough.
[734.572000] sd 3:0:0:0; [sdb] Assuming drive cache: write trough.


Well, thanks in advance,
T-Grave

---

### Post by blueridgedog on 2008-01-02
Not much help, but the only things I could find were 

[https://help.ubuntu.com/community/PSP](https://help.ubuntu.com/community/PSP)

and

[https://help.ubuntu.com/community/UsbFlashDrives#head-ab629b186ed37bedcc58fca245969f4559f17438](https://help.ubuntu.com/community/UsbFlashDrives#head-ab629b186ed37bedcc58fca245969f4559f17438)

Perhaps you could post in the hardware forum.

---

