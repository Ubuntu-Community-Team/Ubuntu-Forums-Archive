---
title: "Should I be worried about  this?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Joe Dinmore on 2007-11-10
I use dial-up (and v7.04). When I look at the "connection Log", I see the following as part of the process:
"
Entering PPP mode.
Async interface address is unnumbered (Loopback0)
Your IP address is 0.0.0.0. MTU is 1500 bytes
--> Looks like a welcome message.
--> Starting pppd at Sun Nov 11 09:43:59 2007
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
"
It's those "Warning"s that are bugging me. Everything is working fine - but could I make it even better?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-10
hello i don't or never have used dial up in ubuntu but i just looks like a permission problem 
its trying to edit system files it dosen't have permission to edit soo
first i would find out if it should be able to edit it. Then ether change the file permisons that the file has or change the permissions the program runs with.
If your a complet noob like most of this i will try to rember how to do this right now i sleepy though
but we or you 
:) would need to find out if it should edit thoughs files

---

### Post by Dark Hornet on 2007-11-10
PAP and CHAP are authentication protocols.  I did a quick search, and found this link which may be able to help you....good luck!!

[http://ubuntuforums.org/archive/index.php/t-98724.html](http://ubuntuforums.org/archive/index.php/t-98724.html)

---

### Post by Irihapeti on 2007-11-11
I've had dialup for several months and I get those error messages in my log all the time. As far as I can tell, they don't make any difference to the working of my connection. As long as it connects, allows you to log in and remain connected, that seems to be all that matters.

HTH

Irihapeti

---

### Post by Bartender on 2007-11-11
I discussed the CHAP/PAP permissions thing here
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

I don't understand the significance of those comments either.

---

### Post by Irihapeti on 2007-11-11
When I first got onto dialup, the big problem I was having was the thing disconnecting straight away. That I fixed by setting stupid mode=on. I seem to recall that *that* means my ISP is doing something odd i.e. not my problem as I see it. (My ISP has done a number of odd things, so that doesn't surprise me.:) )It only relates to the logon process, as far as I can see.

So, unless someone can convince me that ignoring these messages is harmful - and can explain in detail how it's harmful - I'll just go on ignoring them.

---

### Post by Joe Dinmore on 2007-11-12
Thanks everyone. I shall continue to ignore the messages!

---

