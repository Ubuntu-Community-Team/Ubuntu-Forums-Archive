---
title: "Vfat formatted pen drives not showing up on desk top (v6.10) hot plug problem?"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by cogvos on 2006-12-02
](*,) Dear all,
Although I'm not a complete novice I am completely stuck and hope that someone can ,erm, unstick me.

Have just installed umbuntu 6.10 (before coming here to find that it's not recommended for novices... rats). All is ok with the exception of the detection of usb disks, pen drives etc. These are just not detected and do not show up on the desktop. I've used several other flavours of Linux before and they do. So I am guessing its Umbuntu rather than a hardware problem, and probably something glitching in the hot plug system.

Trouble is this is black magic at the best of times and I have no idea where to start.

My system is a Compaq Presario and the pen drives are Vfat formatted. lsusb shows that there is something there (not sure what it actually shows or how it helps).

Could someone point me at a start-point please? Do I check in etc or where and if so what?

Many thanks

John

---

### Post by taurus on 2006-12-02
After you plug it in, look to see which device it is with

Applications -> Accessories -> Terminal
```
dmesg | tail
```
Then, mount it by hand if the automount doesn't work.

---

### Post by cogvos on 2006-12-02
Many thanks for such a quick reply.

Turns out that they are being recognised. But only if they are plugged in after Umbuntu boots. If they are plugged in on boot they don't get picked up. Equally if you disconnect and then replug at this point they still don't get picked up. 

Seems odd. Is there any way of forcing a re-pole or something on boot so that the usb bus is scanned? Seem to remember a problem a while back where there was a timing issue with hot plug devices not being recognised if they were present on boot.

Any ideas?

John.

---

