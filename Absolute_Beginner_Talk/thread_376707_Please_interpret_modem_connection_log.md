---
title: "Please interpret modem connection log"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Michl on 2007-03-05
I am trying to unravel the mystery of my erratic dial-up
under Ubuntu (wheras it is perfect under Windows).  My
connection log (I use gnome-ppp) looks like this (with
IP and DNS addresses deleted):


> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 4523
--> Using interface ppp0
--> local  IP address 
--> remote IP address 
--> primary   DNS address 
--> secondary DNS address 

Can someone please tell me what the Warnings and the bit about
flaky handshakes mean and how this can be corrected?

Thanks,
Michl

---

### Post by ieee488 on 2007-03-05
Try opening up a Terminal window and type **sudo chmod 777 /etc/ppp/pap-secrets**.
I found that wvdial wants to write to that file.
Afterwards you can change that back to 644 if you want.

---

### Post by Michl on 2007-03-05
Thank you -- I'll try it when I get home.  Can't wait.

WOuld there be good reasons for changing it back?
Michl

---

### Post by Michl on 2007-03-06
Turns out the solution was adding:
S19=0 
to the data commands.

---

