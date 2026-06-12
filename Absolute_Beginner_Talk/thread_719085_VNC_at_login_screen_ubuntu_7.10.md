---
title: "VNC at login screen ubuntu 7.10"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by the_genrl on 2008-03-08
well hi there friends!  i use this forum so much i became a member.  still, i need some help though and wasnt able to find this.

I cant seem to VNC into my machine without logging in to the server first.  i followed the procedure listed here > [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC) (in the "VNC Server with Login Screen via GDM" section)
but still no luck.  i tried several procedures similar to this i found on the interwebnets but nothing seems to work.  I am able to login remotely when i login to the server first, but not right when the server is at the login screen.  This is a problem for me.

it did get me farther along though.  now i get a "connection closed unexpectedly" instead of a "connection refused" when trying to log in from my client.  if i try to connect though port 5900 i still get the "connection refused".

any ideas or suggestions will be greatly appreciated.

---

### Post by halitech on 2008-03-08
are you trying to connect from outside your local network? You could try connecting to port 5901 instead of 5900 (mine will only connect on 5901)

---

### Post by the_genrl on 2008-03-09
hi halitech and thanks for responding.  

I should have put that.  i get the "connection closed unexpectedly" when i try to connect through 5901, and every other port including 5900 i get "connection refused".

eventually yes though the internet, but right now both clitent/server are connected directly though a switch.  i feel both are configured correctly (on the ip and lower levels) as i can ping across and even successfully VNC after i get past the login screen at the server.  I can even share files and mount network drives.

the problem is when i just when the VNC server is turned on and is at the login screen.  From the client i cant VNC in.  

Some more info:  the client is running RealVNC on Windows XP and server is vino (im guessing that VNC) ubuntu 7.10.  maybe thats some useful info, but how is it that i can VNC fine after i get past the login screen at the server?


Im guessing this problem is something so simple to...

Best regards,

dave

---

### Post by halitech on 2008-03-09
it might be something between RealVNC and vino. have you tried installing vnc4server (I think thats the right name)

---

### Post by ghost_ryder35 on 2008-03-09
> **the_genrl said:**
> hi halitech and thanks for responding.  

I should have put that.  i get the "connection closed unexpectedly" when i try to connect through 5901, and every other port including 5900 i get "connection refused".

eventually yes though the internet, but right now both clitent/server are connected directly though a switch.  i feel both are configured correctly (on the ip and lower levels) as i can ping across and even successfully VNC after i get past the login screen at the server.  I can even share files and mount network drives.

the problem is when i just when the VNC server is turned on and is at the login screen.  From the client i cant VNC in.  

Some more info:  the client is running RealVNC on Windows XP and server is vino (im guessing that VNC) ubuntu 7.10.  maybe thats some useful info, but how is it that i can VNC fine after i get past the login screen at the server?


Im guessing this problem is something so simple to...

Best regards,

dave

I know that is the problem with Ubuntu desktop, but I thought you didnt have to be signed in for the server... Just SSH into it with PUTTY and call it a day, no reason to remote desktop into a server (unless you have a gui :()

---

### Post by the_genrl on 2008-03-09
hi again guys and thanks for your replies,

halitech:  that might be the case.  my next step is to look into vnc4server, though first i want to find out how it differs from vino-server (session)

ghost_ryder35:  I was thinking of setting up ssh (to login and stuff) for it but was hoping to get accomplish this task directly.  (In the long run, i plan to have VNC through ssh anyway so who knows.)  

The main reason is everything i ever do with ubuntu seems to end up with some hack way of getting around to it.  for ONCE i just want to do something in a clean way...sadly this doesnt look like it's heading in the "clean" direction.

Also, the purpose of this computer is to run a few programs that i think require a gui.  pidgin and DC++ for example.

---

