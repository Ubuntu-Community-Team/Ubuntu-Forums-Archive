---
title: "Logitech Quickcam Pro errors"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2007-11-15
So I FINALLY managed to get pwc to work (or at least I think its working).

The problem I have is that when I plug in my Logitech Quickcam Pro 3000 into my laptop and try and use any video application (e.g. ekiga , skype beta, camorama) the image shows up for a second and freezes then if I check lsusb it won't show up my cam.

lsusb BEFORE using video software:

```

Bus 003 Device 012: ID 1241:1503 Belkin 
Bus 003 Device 011: ID 09da:022b A4 Tech Co., Ltd 
Bus 003 Device 010: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 025: ID 046d:08b0 Logitech, Inc. QuickCam 3000 Pro [pwc]
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

lsusb AFTER using video software:
```

Bus 003 Device 012: ID 1241:1503 Belkin 
Bus 003 Device 011: ID 09da:022b A4 Tech Co., Ltd 
Bus 003 Device 010: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

its as though the computer detects it and then suddenly doesn't. 

Any thoughts? Using gutsy kernel 2.6.22-14-generic, installed pwc by downloading the pwc-source file from syanptic. had to play around with it thought to install it. The pwc.ko file ended up in:
/lib/modules/2.6.22/kernel/drivers/media/video/

instead of 
/lib/modules/2.6.22-14-generic/kernel/drivers/media/video

so i had to copy it over...

otherwise followed EXACT instructions of:

[https://help.ubuntu.com/community/Webcam#head-836881f8aaa64508507ce1f2091b24b8aead02cb](https://help.ubuntu.com/community/Webcam#head-836881f8aaa64508507ce1f2091b24b8aead02cb)

---

