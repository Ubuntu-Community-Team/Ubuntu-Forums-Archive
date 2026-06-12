---
title: "terminal server client"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by tcebak on 2007-11-30
hello guys. 
i am not sure how to terminal server client. i do not know what to put in for username (the computer i'm on or i'm connection to) Username (me or the one i want to connect to) password, domain, client hostname. pretty much newbie questions. but from what i hear you can use RDP for windows.   Although i can connect to a local computer via vncviewer (since the comannd is "vncviewer ip.address.1.1) but i would like to know how to use terminal server client. thanks!!!

---

### Post by gigaferz on 2007-11-30
i used to work  at one place and the guy @ the server had  to set up an account for each user to log in 

if it is RDP or RDPv5 you only need your  the ip of the computer..
thats it, i am talking about windows server 2003.

i just did it right now, and i only entered the ip, the windows server screen wil ask you for user name and password.

using : application->internet->terminal server client

---

### Post by tcebak on 2007-11-30
alright thanks! that was really simple. to typed the ip. but what happens if the computer is not on a local network? still only the ip?

---

### Post by gigaferz on 2007-11-30
well when i was working at that place, i was using my ubuntu to connect to a computer 120 mile away from us, so basically, the trick is to know how to configure the server...
I never did any extra step to have it working, as a client, however on the server side, i dont know.

right know i just tried to log in to that server again and it works and is still like 60 miles away from me.

---

### Post by hyper_ch on 2007-11-30
if you are not on the same network, you'll need to forward the ports accordingly.

---

