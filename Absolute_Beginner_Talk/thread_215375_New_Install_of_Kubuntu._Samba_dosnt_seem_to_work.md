---
title: "New Install of Kubuntu. Samba dosnt seem to work??"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Gamebeavis on 2006-07-13
I installed a fresh copy of Kubuntu tonight, updated my kernel to 2.6.15-26-686 (cause I have a dual core CPU), ran the "recomended" updates, and then installed a series of packages through Automatix. After all this was done I attempted to connect to my Win PC using "smb://192.168.1.100/MediaDrive1" though konqueror, but it gave me this message
"The process for the smb://192.168.1.100 protocol died unexpectedly" and thats it. I went into the samba config file and remembered that I hadnt change MSHOME to my work group, so I proceded to do so. But I still get same message. I cant seem to connect to ANY of my windows machines through smb. Any ideas??

---

### Post by Sonofmoog on 2006-07-13
Can you go the other way?  Do the Windows boxes see the Kubuntu PC?  Open a console, and type 

```
ping 192.168.1.100
```

and see if the other machine answers.  Check the obvious.  Make sure your connection is good, and your router is on.

Open Konqueror and type the IP of your router in the address bar, and make sure it sees the Kubuntu PC ..

In the console, type

```
testparm
```

and let samba reload your smb.conf.  You might also go into system services, stop the smb daemon from running, then restart it, and see if that has an effect.

---

### Post by Gamebeavis on 2006-07-13
Ok, I could ping my PC no problem. I also could log into my router no problem from my linux box. but when I type testparm, this is what I get.. And I have no clue what it means.

beavis@beavislaptop:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
testparm: gconv_db.c:232: __gconv_release_step: Assertion `step->__end_fct == ((void *)0)' failed.
Aborted
beavis@beavislaptop:~$

---

