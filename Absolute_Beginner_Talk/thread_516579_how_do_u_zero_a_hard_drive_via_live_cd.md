---
title: "how do u zero a hard drive via live cd"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by wimpytx on 2007-08-03
any help would be much appreciated

---

### Post by Inxsible on 2007-08-03
> **wimpytx said:**
> any help would be much appreciated
Do you mean you want to format the entire drive ?

Go to System --> Administration --> GParted

That will give you options to hose the hard drive completely

---

### Post by cek on 2007-08-03
Physically "zero"?


assume /dev/sda is the HD you want "zero'd"



from a terminal window:

cat /dev/zero > /dev/sda

you can do the same with other devices:

cat /dev/random > /dev/sda

cat /dev/urandom > /dev/sda

---

### Post by LaRoza on 2007-08-03
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by HermanAB on 2007-08-03
Two ways - boot off a CDROM to ensure that the drive isn't mounted - eg. use Knoppix:
a. There is a program built into all hard drives that will effectively erase the drive.  This is the best way to do it: 
[http://cmrr.ucsd.edu/Hughes/SecureErase.html](http://cmrr.ucsd.edu/Hughes/SecureErase.html)
b. You can actually write zeros to the drive using dd:
$ su -
# dd if=/dev/zero of=/dev/sda bs=16k

The first method is secure.  The second method is OK to enable Windoze to reformat a drive that was previously used for Linux and it will keep most ordinary mortals from reading the old data on the drive.

Cheers,

Herman

---

### Post by Inxsible on 2007-08-03
> **HermanAB said:**
> Two ways - boot off a CDROM to ensure that the drive isn't mounted - eg. use Knoppix:
a. There is a program built into all hard drives that will effectively erase the drive.  This is the best way to do it: 
[http://cmrr.ucsd.edu/Hughes/SecureErase.html](http://cmrr.ucsd.edu/Hughes/SecureErase.html)
b. You can actually write zeros to the drive using dd:
$ su -
# dd if=/dev/zero of=/dev/sda bs=16k

The first method is secure.  The second method is OK to enable Windoze to reformat a drive that was previously used for Linux and it will keep most ordinary mortals from reading the old data on the drive.

Cheers,

Herman
The link doesnt work :(

---

### Post by LaRoza on 2007-08-03
The link is dead...

DBAN, from my first post, will allow you to do a number of things, it does a DoD sanitation by default.

---

### Post by wpshooter on 2007-08-03
or use

[www.killdisk.com](www.killdisk.com)

---

### Post by HermanAB on 2007-08-03
The CMRR seems to be offline - just wait a while.

---

### Post by ugm6hr on 2007-08-03
> **wpshooter said:**
> 
[www.killdisk.com](www.killdisk.com)
Wipes completely  - no probs.

---

