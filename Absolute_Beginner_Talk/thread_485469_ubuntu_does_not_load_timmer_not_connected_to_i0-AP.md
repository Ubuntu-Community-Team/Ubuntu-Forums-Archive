---
title: "ubuntu does not load: timmer not connected to i0-APIC"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by szaemon on 2007-06-26
I have an intermittent problem with Ubuntu Feisty Fawn, upgraded from Edgy. It fails to load. This just happen 10 times in a row and now I'm ack on Windows.

starting up...

[0.464000].. MP- files bug:8254 timer not connected to I0-APIC 
[0.532000] kernal panic- not syncing:I0-APIC plus timmer does't work! boot.ith APIC= Debug and send report then try booting with the "noapic"option
[0.532000]

I would appreciate any help offered.
Thanks

---

### Post by praxis22 on 2007-06-27
I'd try doing what it said, edit grub, either with:

```
sudo gedit /boot/grub/menu.lst
```

or at boot time, (hit escape, follow the prompts) 

Add **noapic** to the end of the line.

More here:

[http://ubuntuforums.org/showthread.php?t=148761](http://ubuntuforums.org/showthread.php?t=148761)

---

### Post by szaemon on 2007-06-27
Thanks I'll try it.

---

