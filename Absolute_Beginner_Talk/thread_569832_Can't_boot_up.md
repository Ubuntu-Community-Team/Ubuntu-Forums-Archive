---
title: "Can't boot up"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by woscafrench on 2007-10-07
I installed ubuntu yesterday with the live cd and I'm able to use the live cd just fine (it's what I'm using now), but whenever I try booting up without it, I'm told there's a disk boot failure. I tried the text based installer, but that came up with the same problem as well.

The only hint I have on what might be wrong is given when on the live cd's list of options I choose to boot from the first hard drive. When I do I'm told:

"MP BIOS bug: 8245 timer not connected to IO-APIC
Kernal Panic - not sincing: I0-APIC + timer doesn't work"

It then recommends I try noapic mode. However, being a complete noob, I haven't the faintest clue how to do that.

---

### Post by jamvegan on 2007-10-07
Try booting normally (without the live cd), and when you see the grub menu, make sure that your Ubuntu installation is highlighted and type "e" (for edit).  Go to the kernel line and add "noapic" to the end, so you end up with something similar to this:
```
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=b497a47a-fd39-41e1-8774-ab4dd239d2f1 ro quiet splash noapic
```
Then type "b" to boot.

If that works, you can make the change permanent by editing the file /boot/grub/menu.lst.  Open a terminal (Applications->Accessories->Terminal) and type:
```
gksudo gedit /boot/grub/menu.lst
```
Enter your password if prompted, then when the file opens scroll down to the first Ubuntu entry and add "noapic" to the end of the kernel line, save and quit.

Best of luck.  I hope this solves your problem!

---

### Post by woscafrench on 2007-10-08
Before getting a response, I tried using a different operating system and installed openSUSE. But the same problem still keeps coming up "Boot disk error Please insert system disk", The funny thing is that if I just leave the installation disk in and choose to boot from the hard disk anyway, everything works ok.

I've tried noapic for openSUSE (I assume that it would have the same affect as in ubuntu) but that doesn't make any difference.

Could this possibly be a hardware problem?

---

### Post by woscafrench on 2007-10-09
bump

---

### Post by overdrank on 2007-10-09
> **woscafrench said:**
> bump

HI, do you have more than one drive? Also do you see the grub before you get the error?

---

### Post by woscafrench on 2007-10-09
I don't see anything before getting an error. It happens as soon as the operating system tries to start up. I have a single hard drive (two dvd-rw drives as well, but i don't think that's what you mean)

---

### Post by oilchangeguy on 2007-10-09
are you sure you actually installed ubuntu? just running the computer from the live cd does not install it. you have to click on the install icon located on the desktop, follow the prompts, reboot, then it's installed.

---

### Post by woscafrench on 2007-10-09
Well, on the the phone to my father he managed to find the problem. For some reason it was set to only boot from my cd-rom drive, so obviously without a disk in there it couldn't do a thing. I have no idea why that was, possibly the manufacturers slipped up.

I'll try re-installing ubuntu, and see if my problems are over. I'll be sure to come back here if there's a problem, (:P) but for now, thank you all for your help.

---

