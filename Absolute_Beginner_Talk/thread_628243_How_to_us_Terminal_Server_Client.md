---
title: "How to us Terminal Server Client?"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Tanjer1588 on 2007-12-01
So i have searched the forums for a while now and i cant seem to find the basics of how to use the TSClient. I have never used any kind of remote access before so i am confused as to what peaces of information to use. I have 4 computers on my network 2 running Ubuntu 7.10 and 2 running windows xp, i have a netgear router that there all hooked up to. i want to be able to accses the windows xp system via TSClient. Allso i dont know what i will be able to do with TSClient, i was reading up on VNC stuff and i have VNC software on the computer but from what i understand i need vnc software on the other computers to beable to remoat accsess them. So i just need to know what information i need in able to access the windows computer via TSClient, such as... "compter" "Protocol" "User name" "Domain" and "client hostname" ... cus i have no idea what to put in any of them

thank you

---

### Post by Tanjer1588 on 2007-12-01
Bump, i really need help with this

---

### Post by bodhi.zazen on 2007-12-01
It is not too hard

You need to enable desktop sharing on the windows side first.

Then open the terminal server client

input you window machine or ip address

choose rdpv5

connect :)

I highly suggest you look at VNC as well.

[http://www.centos.org/docs/4/html/rhd-dg-en-4/s1-ddg-remote-desktop-tsclient.html](http://www.centos.org/docs/4/html/rhd-dg-en-4/s1-ddg-remote-desktop-tsclient.html)

---

### Post by Tanjer1588 on 2007-12-03
Thanks that helped, i did a bit more research and i am able to use my brother computer from my side now, do you know if it is posible to access over the internet?

---

### Post by bodhi.zazen on 2007-12-03
Yes, but if you do that you should consider tunneling over ssh

---

