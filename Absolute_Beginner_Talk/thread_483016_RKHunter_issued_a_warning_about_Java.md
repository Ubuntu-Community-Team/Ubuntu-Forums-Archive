---
title: "RKHunter issued a warning about Java"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-06-24
Hello all,

I ran RKHunter yesterday and everything went fine until it inspected my java files (latest version available) and issued an unspecified warning. What should I do from there? Is it a false positive? If not, how do I fix the problem?

Thanks.

---

### Post by uberushaximus on 2007-06-24
Nothing is wrong, I have the same warning myself, how do you fix it? Remove java if it bothers you. :P

If anyone else knows an alternate workaround feel free to help.

---

### Post by the8thstar on 2007-06-24
More specifically, here is what I got:

> * Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
/etc/.java
/etc/.pwd.lock /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools 
---------------
Please inspect:  /etc/.java (directory)  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 

So... there is NO reason to worry?

---

### Post by jon zendatta on 2007-08-22
i got something similar today.

warning untrusted packages could compromise your system's security.you should only proceed with the installation if you are cetain that this is what you want to do.
sun-java5-bin sun-java5-jre java common unixodbc odbcinstldebian1 libltdl3 gsfonts-x11

but from what was just posted obviously i can go ahead

---

