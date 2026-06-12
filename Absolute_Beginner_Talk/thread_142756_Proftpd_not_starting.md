---
title: "Proftpd not starting"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by animesh on 2006-03-11
animesh@ubuntu:~$ sudo /etc/init.d/proftpd start
Starting ProFTPD ftp daemon:

and it stays there...it was working fine till now......i just added one more user acc. and restarted it and it is giving me this ...... then i removed that user acc. and tried to start it with config. exactly as as it was when it was working......but it still hangs there

---

### Post by taurus on 2006-03-11
What user did you add and perhaps a copy of your proftpd.conf would be nice?

---

### Post by animesh on 2006-03-11
don't know what happened but on rebooting it is working fine
and before rebooting when i saw the system monitor i saw there were 
4 sh in  processes  in which 
sudo /etc/init.d/proftpd stop    was the arguement,no terminal was open  though.

---

