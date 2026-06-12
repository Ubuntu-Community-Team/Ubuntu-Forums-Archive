---
title: "Vpn Pptp"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by hydroIT on 2006-06-14
Hey, first off let me say im quite happy with Ubuntu so far :)

Secondly, I've been googling for some hours, finding different solutions, none of which worked. I'm trying to connect to my ISP, and I know my hardware is fine (working on Windows).

What I know currently about my "needs" and "haves":
I'm trying to connect to an Israeli ISP (Bezeqint, I've seen some subjects about this around here, none with complete solution :E).
I have Motorola SURFboard 4101 Cable Modem.
I'm trying to connect through ETHRENET. (as far as I know - any tests I can do with windows to be sure? ;)).
When setting up the dialer in windows, I set the following:
In **General**: I set the IP needed (being 212.179.61.76).
In **Security**: I choose _Advanced_ and set:
Optional Encryption, and "Allow use of these protocols", I check the following ones: PAP (first selection), SPAP (2nd selection), MS-CHAP v2, (last selection before seperating-line).
In the next tab (network, I think?), I choose "PPTP VPN" in the dropdown combo box.


What do I do to connect to the ISP in linux?

---

### Post by hajk on 2006-06-15
Have you not installed the pptp-linux package? The Windows data that you already have should be sufficient for configuring the pptp client.

---

### Post by hydroIT on 2006-06-15
[QUOTE=hajk]Have you not installed the pptp-linux package? The Windows data that you already have should be sufficient for configuring the pptp client.[/QUOTE]

I have installed the pptp-linux from the synpatic thingie, when I inserted the Ubuntu CD after installation.

---

