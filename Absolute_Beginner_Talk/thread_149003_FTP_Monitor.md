---
title: "FTP Monitor"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by animesh on 2006-03-23
I have been using proftpd and i want a FTP Monitor to see no.of users connected ,speed they are getting and files they are d/lding etc.,etc. as in windows each FTP server has its own monitor, i can't find any such thing for proftpd

I know this is a repost but nobody replied in the previous thread so kindly help me. Atleast somebody must be using a FTP Monitor [-o<

---

### Post by frodon on 2006-03-23
Just use the "ftptop" command (use the "t" character to toggle the monitor to speed rate).
Or you can run gproftpd without root rights (i mean without sudo) thus it will just show you the traffic, i included a .deb in my guide : [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by animesh on 2006-03-23
Thanks a thousand times ..this ftptop command is quite good.

Finally my problem solved

---

