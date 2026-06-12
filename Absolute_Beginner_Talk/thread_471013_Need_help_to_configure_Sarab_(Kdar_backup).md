---
title: "Need help to configure Sarab (Kdar backup)"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by 6kwar on 2007-06-11
Hi all

I am pretty new to Ubuntu. But i think I am doing pretty well. I need to setup a file server. I succeeded to configure Samba and it works just like I wanted.
Now I need to take care of backing up the files. I found this amazing program called Kdar. It does everything I want except for 1 thing. Scheduling. SaraB takes care of it. But I didn't understood how to configure it. And I need help. I read the support but didn't understood how. Searched in google but didn't find any document about it. Something that simplifies it. I succeeded to install Sarab. Didn't got any error messages or nothing  I just need to configure Sarab to schedule every week to backup 4 directories each to a file named Music, Data, Movies and after that the date it was created. And compress it to tar file and split it to 4.3gb. I can do it manually without any problem. And I installed X11Vnc so I can access the server to do it manually. But of course I want it to be done automatically.

Thanks.

Any help and suggestion would be appreciated.

---

### Post by johnny4north on 2007-06-11
this is some documentation on howto sarab [http://sarab.sourceforge.net/](http://sarab.sourceforge.net/)  i dont know much on back ups..  this what im going to be using soon .. [http://www.mondorescue.org/downloads.shtml](http://www.mondorescue.org/downloads.shtml)

---

### Post by 6kwar on 2007-06-11
Thanks.
I will try to use maybe it will be better.

Any other suggestions?

---

### Post by johnny4north on 2007-06-11
no, sorry i m just learning more about linux, i believe that there are really smart people here, but really busy today..:( i will be backing up my system in a few days.  if i find a better solution for you.  i will post it.  good luck.:)

---

### Post by gerscht on 2007-06-11
Take a look at rsnapshot (via apt-get). It's dead easy to configure and yet very flexible. The configuration is in /etc/rsnapshot.conf afer installation.
If you're interested I can post a script and some modifications in HAL rules which trigger an backup to an USB disk automatically once plugged in.

---

### Post by 6kwar on 2007-06-12
That would be great.

I read about rsnapshot. it backs up data but not in the way I want. I need it to be tar and split it to 4.3gb (DVD5).
You gave me a great idea to another project that I am thinking about, But on this server I must use tar and split it to 4.3 for DVD backup.

Thanks again.

---

