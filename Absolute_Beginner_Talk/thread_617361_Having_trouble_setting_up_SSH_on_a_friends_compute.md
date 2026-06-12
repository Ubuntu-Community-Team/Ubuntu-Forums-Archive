---
title: "Having trouble setting up SSH on a friends computer"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-11-19
I'm having trouble setting up SSH on my friends computer.  I set up his computer with a static internal IP, forwarded port 80 to that IP, and installed the open SSH client and server.  The settings are almost identical to my PC at my house, but the connection always times out on his.  Any idea what could be wrong?

He lives in an apartment not affiliated with our college campus, but his internet is through the campus' network (I assume the apartment complex has some kind of deal with campus).  Is there any way to block incoming SSH traffic?  I changed the port in the SSH config file to 7032 (arbitrary port) and also the forwarding and it still didn't work.  

Any ideas?  I'm pretty new to this, but I set up SSH on my PC at home very easily and couldn't believe I couldn't get it to work on his.

---

### Post by brennydoogles on 2007-11-19
> **TheOrangePeanut said:**
> I'm having trouble setting up SSH on my friends computer.  I set up his computer with a static internal IP, forwarded port 80 to that IP, and installed the open SSH client and server.  The settings are almost identical to my PC at my house, but the connection always times out on his.  Any idea what could be wrong?

He lives in an apartment not affiliated with our college campus, but his internet is through the campus' network (I assume the apartment complex has some kind of deal with campus).  Is there any way to block incoming SSH traffic?  I changed the port in the SSH config file to 7032 (arbitrary port) and also the forwarding and it still didn't work.  

Any ideas?  I'm pretty new to this, but I set up SSH on my PC at home very easily and couldn't believe I couldn't get it to work on his.

It could very well be that the university is blocking the ssh from working. First step may be to contact Campus OIT and see if they are blocking it, and if they are, see if they will allow you to bypass whatever they are using to block it. I hope this helps!

---

