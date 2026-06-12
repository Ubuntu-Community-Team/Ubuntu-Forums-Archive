---
title: "Bluetooth Mouse/Keyboard on 9.10"
date: 2009-11-02
forum: Apple Hardware Users
---

### Post by kmand on 2009-11-02
I have an Apple Bluetooth Keyboard and Mouse on a Mac Mini. On 9.04 I had

HIDD_ENABLED=1
HID2HCI_ENABLED=0
HIDD_OPTIONS=" --server --connect 00:0A:95:3A:82:8D --connect 00:0A:95:0A:E6:36"

in my /etc/default/bluetooth file, and they connected on boot and stayed connected.

On 9.10 with the same file, they don't auto connect. I can force them to connect with "hidd -connect xx:xx:xx:xx:xx", but they disconnect after a while.

Any thoughts?

---

### Post by tyce on 2009-11-05
I'm having the 'same' problem (only I can't even force it to connect any longer).

Anyone with the answer?

thanks.

---

### Post by tyce on 2009-11-05
So I'm not sure what I did, but I kept forcing the connect and hitting the power button and random keys on the keyboard...  Long end of the short...  It finally picked up.

I'll let you know if it stays that way.  G'luck.

---

### Post by tyce on 2009-11-06
didn't last, back to square one, although this article has been helpfull:

[http://ubuntuforums.org/showthread.php?t=224673](http://ubuntuforums.org/showthread.php?t=224673)

---

### Post by zackpuse on 2010-01-18
i have same problem bluetooth mouse stop function need too reboot my compaq presario v3000. i use 2.4g wireless optical mouse.i problem make big problem to me when i do some important job

---

### Post by anothergene on 2010-01-25
> **kmand said:**
> I have an Apple Bluetooth Keyboard and Mouse on a Mac Mini. On 9.04 I had

HIDD_ENABLED=1
HID2HCI_ENABLED=0
HIDD_OPTIONS=" --server --connect 00:0A:95:3A:82:8D --connect 00:0A:95:0A:E6:36"

in my /etc/default/bluetooth file, and they connected on boot and stayed connected.

On 9.10 with the same file, they don't auto connect. I can force them to connect with "hidd -connect xx:xx:xx:xx:xx", but they disconnect after a while.

Any thoughts?

bump

I have the same problem with Karmic.  They do connect to the hardware as I can use the keyboard to change boot sources with Refit.  don't work once ubuntu boots.

A fix would be much appreciated!

---

### Post by linuxopjemac on 2010-01-25
did you try blueman?
```

sudo apt-get install blueman
```

---

