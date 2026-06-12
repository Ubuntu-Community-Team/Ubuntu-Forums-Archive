---
title: "How to boot from installer on thumbdrive?"
date: 2017-12-06
forum: Apple Hardware Users
---

### Post by sterator on 2017-12-06
I still have the USB installer I used to install ubuntu onto a Mac of mine. Is there a procedure to get the computer to boot to that usb installer?

I tried by inserting the stick into the machine, then powering up, but all I got was a blank screen.

thank you for any help on this!

---

### Post by ratell on 2017-12-06
You would need to hold option while the computer is booting and select the thumb drive as the startup drive.

---

### Post by C.S.Cameron on 2017-12-06
If the problem is due to an ISO9660 image on the drive you can use mkusb to zero the first MB on the drive or use GParted to create a new partition table.

[https://askubuntu.com/questions/981119/usb-is-locked-cant-be-written-to-or-formatted-after-using-it-to-make-a-live-u/982396#982396](https://askubuntu.com/questions/981119/usb-is-locked-cant-be-written-to-or-formatted-after-using-it-to-make-a-live-u/982396#982396)

---

### Post by sterator on 2017-12-06
How would I know if a problem is due to an ISO9660 image? How would one determine that?

Thank you!

---

