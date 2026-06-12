---
title: "no picture after install fisty fawn"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-07-22
i put HD in an older computer i have at first it said there was a problum with x server i fiddled with it now it boots up i can hear ubuntu sounds but theres no pic after boot up

---

### Post by Seisen on 2007-07-22
Did you install Ubuntu when the hard drive was in the old computer or before it was put in the old computer?

---

### Post by trucker33377 on 2007-07-22
it was b4 and up and runing well

---

### Post by ReaderRat on 2007-07-22
You may be running the wrong driver(s) for your display.

Are you using the same monitor for both computers, or are there different monitors for them?

---

### Post by trucker33377 on 2007-07-22
there not the same

---

### Post by alienexplorers on 2007-07-22
Please list your xorg.conf file
> cat /etc/X11/xorg.conf

---

### Post by ramjet_1953 on 2007-07-22
With any operating system it is unlikely that you can just pull a hard drive out of a system and put it into another system, with completely different hardware.

It just doesn't work that way.

When you install an operating system, the installer probes your hardware and either automatically installs the required driveres for that hardware, or prompts you to load them manually.

You will almost certainly need to re-install on that particular machine.

Regards,
Roger :cool:

---

### Post by trucker33377 on 2007-07-25
> **ramjet_1953 said:**
> With any operating system it is unlikely that you can just pull a hard drive out of a system and put it into another system, with completely different hardware.

It just doesn't work that way.

When you install an operating system, the installer probes your hardware and either automatically installs the required driveres for that hardware, or prompts you to load them manually.

You will almost certainly need to re-install on that particular machine.

Regards,
Roger :cool:

As i was driving home from work today I was thinking the same thing DUH! IT looks at all the hardware as it installs, Is there  command to get it to relook?

---

### Post by 3rdalbum on 2007-07-25
When you get the blank screen, press Control-Alt-F1.

You will get a text console screen. Log into it if necessary, and then type:

```
sudo dpkg-reconfigure xserver-xorg
```

Accept the defaults. After the program has finished, reboot the system:

```
sudo reboot
```

If you still get the blank screen, run the first command again, but this time when it asks about autodetection, say no both times. Select the video driver "vesa", and the "simple" mode of configuring the monitor.

---

