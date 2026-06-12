---
title: "Trying to install Tux Commander in Dapper"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by elaich on 2007-02-22
I found a .deb, and ran dpkg in terminal, and got this message:

status database area is locked by another process

Anyone know what this means, and how to get around it?

---

### Post by annda on 2007-02-22
it means that probably some other install-database-using process is running. close synaptic if you have it running (or update-manager). if not, log out and log in again and repeat the command. if that does not help, reboot.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-02-22
Close out any other programs that might have control of the file your attempting to run/install! If there are no other programs running during the install, verify any processes running in the background that could potentially have a lock on this particular file. 

$ps aux

If your not able to see anything, try and reboot. If that doesn't work, please post back to the forum. 

Regards,

---

### Post by elaich on 2007-02-22
Thanks. I had Synaptic running.

---

