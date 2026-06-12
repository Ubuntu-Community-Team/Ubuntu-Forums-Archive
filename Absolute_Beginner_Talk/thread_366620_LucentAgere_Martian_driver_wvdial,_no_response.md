---
title: "Lucent/Agere Martian driver wvdial, no response"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Bushfire on 2007-02-21
Hi,
I'm trying to setup my dial up connection in Linux. It is a Agere Systems 56k WinModem, as reported by ScanModem. I have installed martian_dev, and martian_modem, and it gives it a port of /dev/ttySM0. I am using the wvdial.txt produced by ScanModem.

However, when I run sudo wvdial, It tries a couple of initialization commands, then informs me that "Modem not responding"

Any ideas? I'm running Ubuntu Edgy, 2.6.17-10.

Cheers,
-Bernard.

---

### Post by edgarde on 2007-02-27
Have you tried this thread: [http://ubuntuforums.org/showthread.php?t=332947](http://ubuntuforums.org/showthread.php?t=332947) ?

What device is wvdial trying? You might need to link it (usually /dev/modem) to /dev/ttySM0 .

Es.

---

