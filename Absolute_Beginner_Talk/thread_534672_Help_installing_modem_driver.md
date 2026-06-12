---
title: "Help installing modem driver"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Kilobyte on 2007-08-25
Hello.  I recently installed Ubuntu 7.04 on a computer, and got a Linux compatible modem.
So, anyways, I believe the drivers are for a 2.4 kernel, and Ubuntu is a 2.6, correct?
So, could I install the 2.4 kernel drivers, or should I download them from here:
[http://www.heby.de/ltmodem](http://www.heby.de/ltmodem)
This is my modem:
[http://secure.stratitec.com/product_info.php?cPath=6_135&products_id=830](http://secure.stratitec.com/product_info.php?cPath=6_135&products_id=830)
Also, how does one go about installing a modem? :confused:
I'm rather n00b at Linux, but I hope to replace Windows with Linux, soon, on this PC.
Thanks for the help.

---

### Post by linuxwizard on 2007-08-25
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by Kilobyte on 2007-08-25
Thanks for the link, but as I'm really n00b-ish, I need some help deciphering what to do for the Lucent drivers.
[https://help.ubuntu.com/community/DialupModemHowto/Lucent](https://help.ubuntu.com/community/DialupModemHowto/Lucent)

Could explain what to do, perhaps in more layman's terms?
For example, do I run this:
# sudo aptitude install linux-386 
# sudo reboot

Under the run command, or do I go to the X-Window?
Also, the CD I have has 2.4 kernel drivers, would those work, and how would I install them?

Thanks for the help.

---

### Post by linuxwizard on 2007-08-25
In a terminal 
sudo aptitude install linux-386 
sudo reboot

---

### Post by Bachstelze on 2007-08-26
Forget that and use the Martian driver, which is described later on the page, as it is much more reliable.

---

