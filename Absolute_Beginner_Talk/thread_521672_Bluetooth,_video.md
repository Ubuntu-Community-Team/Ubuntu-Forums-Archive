---
title: "Bluetooth, video"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by satnampenaich on 2007-08-09
Hi, I just installed linux on my computer and now my bluetooth keyboard and mouse from logitech doesn't work. I was wondering if there is a way to fix that. Also, I have a video card with a DVI, S-video, and VGA output but with windows operating system, I was able to clone, have multi outputs and be able to view more than more screen at the same time. I would really help me out if somebody can help me out with this. Thanks for taking your time out.

Satnam

---

### Post by annda on 2007-08-09
hi and welcome!

this should help you with the bluetooth problems:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

and we need to know exactly what your video card is - the solutions are different for different cards...

if you can't find it out, you can try this command run in the terminal (applications>accessories>terminal):
```

lshw -C display
```

---

### Post by satnampenaich on 2007-08-09
Thank you, 
I tried using the bluetooth setup but didnt work. I also called logitech and they said it wasnt compatible with linux. Here is the information on the video card.

you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@01:00.0
       version: a1
       size: 128MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: latency=64 maxlatency=1 mingnt=5
       resources: iomemory:fd000000-fdffffff iomemory:e8000000-efffffff irq:11

---

### Post by annda on 2007-08-09
take a look at this:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

it seems your card needs the nvidia driver. for multi-monitor support install the driver and for configuration use
```

gksudo nvidia-settings
```

---

