---
title: "PLF replacements for w32codecs???"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-29
I had the plf freecontrib repository and the w32codecs with dapper and the edgy betas/RC's, then I ruined my computer messing around with Beryl/aiglx so had to do a re-install from scratch...well now I can't get the w32codec, and I also tried this:

wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)
sudo dpkg -i w32codecs_20060611-0.0_i386.deb

anybody got a helpful hint?

---

### Post by meng on 2006-10-29
The wget and dpkg strategy worked for me yesterday on my edgy install, what trouble did you run into?

---

### Post by crimesaucer on 2006-10-29
this is the error:

peep@show:~$ wget -c [http://www.debian-multimedia.org/poo...1-0.0_i386.deb](http://www.debian-multimedia.org/poo...1-0.0_i386.deb)
--21:14:07--  [http://www.debian-multimedia.org/poo...1-0.0_i386.deb](http://www.debian-multimedia.org/poo...1-0.0_i386.deb)
           => `poo...1-0.0_i386.deb'
Resolving [www.debian-multimedia.org](www.debian-multimedia.org)... 213.186.33.16
Connecting to www.debian-multimedia.org|213.186.33.16|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...1-0.0_i386.deb](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...1-0.0_i386.deb) [following]
--21:14:08--  [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...1-0.0_i386.deb](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...1-0.0_i386.deb)
           => `poo...1-0.0_i386.deb'
Resolving ftp.sunet.se... 194.71.11.70, 2001:6b0:19::64
Connecting to ftp.sunet.se|194.71.11.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:14:09 ERROR 404: Not Found.

peep@show:~$ sudo dpkg -i w32codecs_20060611-0.0_i386.deb
dpkg: error processing w32codecs_20060611-0.0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20060611-0.0_i386.deb
peep@show:~$

---

### Post by crimesaucer on 2006-10-29
I'm sorry I think something changed when I pasted:

wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)

***it's downloading now so hopefully it will work, sorry.***

---

### Post by meng on 2006-10-29
No problem, hope it all works out.

---

### Post by crimesaucer on 2006-10-29
It did, but now my xine does a weird blotchy stripped thing when it connects to a video stream, then it plays it perfectly. I'll mess around a bit and see if it fixes the problem, thanks for the help and should I take the plf repository off of my sources.list now?

---

### Post by meng on 2006-10-29
Can't hurt to comment out that line (with #) in your sources.list for now, and reactivate it later if you need it.

---

