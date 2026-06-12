---
title: "Need help to get wireless card working"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-02-23
I'm using 6.06 and I want to get my wireless card working, if possible.  I have no idea how to go about doing this.  The card is a Broadcom 54g MaxPerformance.

---

### Post by Matt1632 on 2007-02-24
Is my wireless card even supported?

---

### Post by Bachstelze on 2007-02-24
It might be. What type of card is it (USB, PCI, PCMCIA...) ?

---

### Post by Matt1632 on 2007-02-24
Well, It''s inside my laptop.  I guess it's PCI then, right?

---

### Post by Bachstelze on 2007-02-24
Type tis in a terminal

```
sudo iwconfig
```

is your wireless detected ? If so, you should only need to run fwcutter to get the firmware from a Windows driver. If not, you'l have to use ndiswrapper.

---

### Post by Matt1632 on 2007-02-24
The output of that was ```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```
I'm new to linux, so i'm going to need a little help with the programs/drivers.

---

### Post by Bachstelze on 2007-02-24
So your cad works with the bcm43xx driver. All you should need is [here](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx).

---

### Post by thehodgie on 2007-02-24
I don't know if this will help or not, but: [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

