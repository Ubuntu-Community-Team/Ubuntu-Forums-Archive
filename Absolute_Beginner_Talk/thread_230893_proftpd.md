---
title: "proftpd?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by ThePolkapunk on 2006-08-06
I'm trying to get an FTP server onto my ubuntu 6.06 server machine.  The tutorial I'm using explains how to use proftpd, but I'm having some problems getting it on.  Searching around on the internet, I keep finding that I can install it using "sudo apt-get install proftpd", or to use synaptic.  Trying to install it from the command line gives me a message that it can't find "proftpd," and the program isn't listed in synaptic.  Was this program removed Ubuntu?

---

### Post by cstudent on 2006-08-06
Do you have all the repositories enabled? Look in synaptic under settings>>repositories. That should give you the ability to install proftpd. I would also recommend installing gproftpd too. It gives you a graphical interface with proftpd.

---

### Post by fene on 2006-08-06
No, it's not removed from the ubuntu list. It's probably just in an list that is not used by default.

Edit your /etc/apt/sources.list and uncomment all repositories. Afterwards you shoud be able to install the program using the command line or synaptic.

---

### Post by ThePolkapunk on 2006-08-06
Thanks a lot guys!  I was able to install proftpd and I also installed the GUI version.  Thanks for all your help!

---

