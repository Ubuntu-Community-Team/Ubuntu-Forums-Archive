---
title: "[SOLVED] Terminal Server Client Problems"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2006-09-21
I can't figure out how to do a print screen with Ubuntu yet..:confused: 


When I try to use the Terminal Server Client to connect to one of my XP boxes running Remote Desktop, I get an error saying "You are attempting to connect back to your own computer.  The requested operation is not allowed."

I am entering an internal IP when doing this....192.168.0.8  I can connect fine from any other XP box inside or ourside of my network, but not from Ubuntu.  What do I need to change?

Also, what is a good VNC client to use in order to remote INTO my Ubuntu box from a XP box?

---

### Post by kc5hwb on 2006-09-21
bump

---

### Post by [S|G] on 2006-09-21
What is the IP address of your ubuntu box? Did you specify it manually? And, are you sure you didn't choose the same IP for both machines?

---

### Post by kc5hwb on 2006-09-21
The IP of my Ubuntu box is 192.168.0.82.  The IP of my XP box is 192.168.0.84.  I have the statically assigned to each specific MAC.  Also, I didn't think you could RDP into an Ubuntu box, I have tried that and can't get it to work.

Plus, when the login window comes up, it says "windows xp" and I enter my username and password, then I get that error.

---

### Post by [S|G] on 2006-09-21
You can't actually RDP into a linux box... You can use VNC for that however. About the error... if the windows login prompt shows up, it means you're already connected to that machine, so it must be some configuration (or rather misconfiguration) on the windows server.

Is that the exact error message? I have googled for it and didn't find a single match...

---

### Post by kc5hwb on 2006-09-21
Thats the exact error, word for word.  And it can't be a problem in the windows server, because it works from any other XP both, both inside and outside of my network.  The only way it doesn't work is if I try to connect from Ubuntu.

---

### Post by hamstersquasher on 2007-06-09
I had this same problem too and I got around it by using RDPv5.  I don't know why this works but it does!

---

### Post by twizler on 2007-11-10
SOLVED --
> 
In the [SIZE="2"]Terminal Services client[/SIZE] - **on Linux **next to  
[SIZE="4"] Protocol click DROP DOWN --select ==  RDPv5[/SIZE]

Had the same thing !! WOW WORKING NOW:popcorn:

---

### Post by humptybump on 2007-11-30
Thanks - I had this same issue. :KS

---

### Post by Yer_Grannie on 2008-02-03
Same here...

---

