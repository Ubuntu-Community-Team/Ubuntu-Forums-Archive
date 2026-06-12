---
title: "Installation blues"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by rakesh343 on 2007-12-17
I am using UBUNTU 7.04 and recently acquired the new version UBUNTU 7.10. but when I tried to install by booting directly from the CD, it displayed a list of errors which looks something like SQUASHFS ERROR. It continued nonetheless and again got stuck with my screen showing a notice that 

THE DISPLAY SERVER HAS SHUT DOWN 6 TIMES IN LAST 90 SECONDS. IT SEEMS SOMETHING BAD IS GOING ON. IT WILL TRY AGAIN IN TWO MINUTES.

 Nothing happened afterwards and I had to force a shut down. What's wrong?

---

### Post by jken146 on 2007-12-17
Is this when you're trying to boot from the live CD?  If it is, then it could be a bad download or burn.  Did you:
- check the md5sum of your downoad?
- run the CD integrity check?

---

### Post by rakesh343 on 2007-12-17
The CD is alright. I got it shipped from the Canonical Limited. The check for defects in the CD did not show anything wrong. In fact on other machines too it showed similar list of errors.

---

### Post by jken146 on 2007-12-17
Tried safe graphics mode?

Perhaps try an alternate CD (text based installer only).

---

### Post by Sef on 2007-12-17
> The CD is alright. I got it shipped from the Canonical Limited. The check for defects in the CD did not show anything wrong. In fact on other machines too it showed similar list of errors.

Ship-it disks can be bad.  If the same error is happening on different machines, it is almost certainly a bad disk.

---

### Post by rakesh343 on 2007-12-17
> Ship-it disks can be bad. If the same error is happening on different machines, it is almost certainly a bad disk.
__________________

But the "Check the disk for errors" does not show any errors!!!

---

### Post by skyjacker on 2007-12-17
Are you able to connect to the internet? If so download an .iso file. Burn this file to a cd, check it for errors, and try the install using this new cd. Remember to burn using a SLOW speed. K3B is a good burn program to use, or right click on the file and choose "burn iso file"   Good Luck

---

### Post by jken146 on 2007-12-17
> **rakesh343 said:**
> But the "Check the disk for errors" does not show any errors!!!

It is not infallible unfortunately.

---

### Post by erginemr on 2007-12-17
Please see the following thread:

[http://ubuntuforums.org/showthread.php?t=639805](http://ubuntuforums.org/showthread.php?t=639805)

and go grab the "alternate" installation CD (i.e. its ISO file from the net). 

(The problem has something to the with a too high initial boot -up resolution.)

---

