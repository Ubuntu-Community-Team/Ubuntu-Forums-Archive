---
title: "SDA Nowhere To Be Found. USB Devices Not Recognized."
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by maatghandi on 2005-11-27
I am new to ubuntu, but have used Fedora in the past. I installed 5.10 last night. Everything sems to be running smoothly except I can't get any USB device to be recognized. I read that Ubuntu has this udev thing going. Yet, udevinfo provides no information for me to write any rules because there are no sda devices to be found anywhere.
I am trying to mount a printer and an external hard drive, both usb. Unfortunately neither were automounted, and it appears that the OS has no clue that they are there. I know the printer and hd work, and I know the cables are good. I know the usb ports work too because I had Win 98 on here and it read the hd just fine (didn't have the printer yet). Any ideas?

Thanks,
Jerome

---

### Post by ssam on 2005-11-27
i think fedora uses udev these days as well. with udev the /dev/sda type device nodes are only created when you plug something in.

the printer does not need to be mounted. if it is supported by cups then you should be able to plug it in and print (just try an print from any program). sometimes you may need to have a poke in system -> administration -> printers to get it working.

the usb drive should also be recognised and mounted automatically. can you open a terminal, plug in the drive and type the following command in the terminal

```
dmesg | tail -n 20
```

and post the output.

---

