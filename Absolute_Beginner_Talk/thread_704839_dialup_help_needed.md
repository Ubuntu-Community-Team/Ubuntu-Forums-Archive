---
title: "dialup help needed"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by johnwen on 2008-02-22
Anyone know how to grant permission to the PAP and CHAP files for the ISP?  Access is very slow for me.
Thanks,
John

Your IP address is 0.0.0.0. MTU is 1500 bytes
--> Looks like a welcome message.
--> Starting pppd at Sat Mar 22 18:51:41 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 19492



:guitar:

---

### Post by S15_88 on 2008-02-22
have a look at this [https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")

might help you out.

Thanks, Alain

---

### Post by spiderbatdad on 2008-02-22
run wvdial with sudo.

---

