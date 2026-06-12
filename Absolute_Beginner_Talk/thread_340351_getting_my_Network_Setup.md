---
title: "getting my Network Setup"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by happyhacker on 2007-01-17
I have installed SWAT and below is the inetd.conf file. I can't get SWAT running on [http://localhost:901/](http://localhost:901/). FFox just reports 'not foung'

What do I do next?

#<off># netbios-ssn stream tcp nowait root /usr/sbin/tcpd /usr/sbin/smbd
swat stream tcp nowait.400 root /usr/sbin/tcpd /usr/sbin/swat

---

