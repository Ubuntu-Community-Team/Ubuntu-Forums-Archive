---
title: "How to Manually Mount a Windows Mobile Device"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by plinydogg on 2007-10-30
Hi everyone,

As part of my attempts to learn how Linux works I'm messing around with the *mount* command. I figured a good place to start would be to try to mount my Windows Mobile (ttyUSB0) device's filesystem. 

I thought that WM2003SE devices used a RAW filesystem format and so I attempted to mount it using this command:

```
sudo mount -t RAW ttyUSB0 /home/
```

I got an error saying that the 'RAW' filesystem was unknown. I tried using FAT32, FAT16, etc. instead but got the same error. 

Does anyone have any advice? I know about SynCE, etc. but I was hoping to use this as a learning experience...

Thanks in advance,

Plinydogg

---

### Post by damotor on 2007-11-02
Try this:
> sudo synce-serial-abort
sleep 5
sudo synce-serial-config ttyUSB0
sleep 5
raki
sleep 5
sudo synce-serial-start
sleep 5
multisync
if ti says it can't found any program install it from synaptic

---

### Post by plinydogg on 2007-11-02
Thanks damotor! I think it only partially worked though. I got a bunch of error messages (even after I installed all necessary packages). I guess I'll keep messing around with it and abandon my hopes to do it without using SynCE...

---

