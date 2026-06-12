---
title: "Permission problems DIP/DIALOUT"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Brian Fisher on 2008-01-20
Permission problems with DIP and DIALOUT groups using Ubuntu 7.04.

1.  When I try to dialout using the pon command, I get the following:
brian@dell:~$ pon
Error: only members of the 'dip' group can use this command.
When I try to add myself or other users, I get this:
brian@dell:~$ sudo adduser brian dip
Password:
The user `brian' is already a member of `dip'. 
However, I can dial out if I use sudo pon.

2.  Also when dialing out using wvdial, the modem connects briefly and then:
--> Unable to run /usr/sbin/pppd. 
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf. 
I can successfully dial out if I use sudo wvdial.

3.  Using kppp I have a similar problem:
Can't open options file /etc/ppp/peers/kppp-options: Permission denied

How do I use these dailup tools other than as root?  None of the tools seem to recognize the users who are already members of DIP and DIALOUT?

---

