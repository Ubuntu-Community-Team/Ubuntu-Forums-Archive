---
title: "Samsung MFC not installing"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by cy83r0n1n on 2006-11-13
Hi guys, just a quick one.

I have a Samsung MFC SCX4521 which is a great printer as Samsung are nice enough to make Linux Drivers for it.

Previously I had CentOS 4.4 due to its stability, but was forced to change due to its php, mysql and Samba being out of date for some time now.

I currently have Ubuntu Server 6.10 32bit running on a AMD 64bit dual core (64bit OS's still have a bit of maturing to do) and I cant get this printer working for the life of me. I had no problems with CentOS.

OK, I had the same problem as the guy in this post
[http://www.ubuntuforums.org/showthread.php?t=232276](http://www.ubuntuforums.org/showthread.php?t=232276)
So I copied the file to the correct directory and it didnt give me that error again the next time I tried to install it.

now... When I enter 
> lpr -Pscx4100 bw\.ps
into the console I get..
> slpr.bin: cannot connect to X server 

.. command failed!

Once again, I dont have X because its a server and not needed.

any ideas?

---

