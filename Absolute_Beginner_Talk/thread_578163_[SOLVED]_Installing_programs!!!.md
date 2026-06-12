---
title: "[SOLVED] Installing programs!?!?!?"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Beryan on 2007-10-16
Hey everyone, I have just began using linux, and I am having some troubles. First of all, it seems like i'm not able to install any new programs. There may be some extremely simple fix to this, but I have looked through the forums, and have not been able to find one. When I attempt to install updates, it tells me an error has occured, and "E: dpkg was inturrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report." I have run the command specified in the terminal, and it tells me "the requested operation requires superhuman privilige". Also, when I try to install a program that I have downloaded, it tells me that "only one software management tool is allowed to run at the same time." The downloaded installer has a .deb file extension, and I would appreciate it if someone could help me out!

I might hit two birds with one stone here. When i try to access files from my linux partition, it tells me that I do not have the rights to do so. How can I change who can view and change my files on linux? Thanks!

---

### Post by adamorjames on 2007-10-16
Try "sudo dpkg --configure -a" :)
About the other problem, '...it tells me that "only one software management tool is allowed to run at the same time.' that usually happens when you have Synaptic open or some other pkg getter :D.
Not totally sure about the last problem. I've read about it but never really needed to mess with the permissions yet. So no experience.

---

### Post by aysiu on 2007-10-17
Paste the command ```
sudo dpkg --configure -a
``` into [the terminal](http://www.psychocats.net/ubuntu/terminal). When you're asked for a password, enter your password.

Further reading:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by Sef on 2007-10-17
Applications > Accessories > Terminal

then enter this command:

```
sudo dpkg --configure -a
```

enter


then type your password (which will not be shown.)

After that you should be able to install any program.   If not, it works or not, please let us know.

---

### Post by Beryan on 2007-10-17
Thanks a lot guys! Everything works great!

---

