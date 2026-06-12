---
title: "Useing dialup internet on ubuntu ?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by hamishnz on 2007-08-11
I have just installed Ubuntu on a friends computer.
He uses dialup internet.
Could someone please guide me though the steps of setting up dialup.
Also, how do you dial the connection ?

Thanks so much,

Hamish

---

### Post by Zalbor on 2007-08-11
System>Administration>Network has a modem connection there, setting it up would probably work.

---

### Post by Bartender on 2007-08-11
> **Zalbor said:**
> System>Administration>Network has a modem connection there, setting it up would probably work.
That hasn't worked since Dapper.
Try [this]("http://ubuntuforums.org/showthread.php?t=480717") for the software end of it.  Chances are very good that his modem won't work, or at least it won't work without a lot of screwing around.
Who's the ISP?

---

### Post by Zalbor on 2007-08-11
Sorry, I've not had dial-up since Breezy...

Before then I needed options for dialup that this method didn't (and still doesn't) have, so I used another one. Maybe that one still works?
Open a terminal and type "sudo pppconfig". Add a connection using the guide there. Then you can connect and disconnect using "pon <connection name>" and "poff".
For example, if you named the connection "conn", "pon conn" will connect and "poff" wil disconnect.
I've no idea whether that still works, but it can't hurt to try...

---

