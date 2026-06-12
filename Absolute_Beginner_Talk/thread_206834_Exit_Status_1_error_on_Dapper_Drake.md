---
title: "Exit Status 1 error on Dapper Drake"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by Madmat on 2006-06-30
I have recently installed Dapper Drake on a network computer and configured the modem to call my ISP.  I querried the modem first to make sure that all was well inside the box.
The modem dial out (dial-up), does its handshaking with the host and then disconnects giving me the "Exit Status: 1" error code.
When I ask for the logfile it says:

   Jun 25 16:26:03 ubuntu pppd [7600]:  The remote system is required to            authenticate itself but I couldn't find any suitable secret (password) for it to use to do so.  (None of the available passwords would let it use an IP address).

I have disabled the network connection to my Windows computers and still get the same result.
I have tried PAP/CHAP, PAP, CHAP - all with the same results.
Anybody have any suggestions that I may try?  Thank you

---

### Post by Apple 101 on 2006-07-01
Check that Windows can connect, and use the same username/password.

---

### Post by Madmat on 2006-07-01
Thank you Apple,
I can see the XP from Linux, but not vice versa.
I am using the same passwords for both networks.

---

