---
title: "Connecting to home pc remotely in Gutsy"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by tonycm1 on 2008-01-15
I want to connect from work (using win2k) to my home machine (ubuntu 7.10) using some sort of remote software tool...  can someone point me in the right direction of how i'd be able to do this?

---

### Post by carverj on 2008-01-15
Are you just looking to transfer files between them?
Because at home I have a NAS server which uses CIFS to communicate/interoperate.
The tool I use on XP is called WinSCP.

---

### Post by tonycm1 on 2008-01-15
I was actually hoping for something that would allow for remote desktop control.... i used to use Radmin in when my PC used to be windows xp... but since switching to Ubuntu, I haven't been able to find an alternative so that I can still remote from work :(

---

### Post by nikoPSK on 2008-01-15
There is ssh, vnc and remote desktop. :)

---

### Post by carverj on 2008-01-16
Do a google on the following string 'ubuntu remote desktop control program'.
It has some interesting reads on the subject!

---

### Post by nikoPSK on 2008-01-16
remote desktop and vnc are easiest. :)

---

### Post by eolson on 2008-01-16
+1 for VNC

---

### Post by tonycm1 on 2008-01-16
Just set up the "Remote Desktop" in System --> Preferences --> Remote Desktop

Took no time at all and works great WITHIN my house....

How do I know what port this program uses so that I can forward it on my router so that I can access this using my external ip instead of the 192.168.... ??:confused:??

---

### Post by tonycm1 on 2008-01-16
Fixed it!

For future reference, if anyone wants to use the Remote Desktop function in System --> Preferences, it uses port 5900 by default so forward that on your router and your set :)

I'll test it at work tommorow and mark this as "solved" once I confirm :)

---

### Post by nikoPSK on 2008-01-16
> **eolson said:**
> +1 for VNC

:p

> **tonycm1 said:**
> Fixed it!

For future reference, if anyone wants to use the Remote Desktop function in System --> Preferences, it uses port 5900 by default so forward that on your router and your set :)

I'll test it at work tommorow and mark this as "solved" once I confirm :)

glad you fixed and that I could help. :)

---

### Post by PartisanEntity on 2008-01-21
I tried setting this up today so that I could access my Gutsy laptop from work (win xp).

I was not able to log in to my laptop though, using VNC Viewer I get:

> unable to connect. connection timed out

---

