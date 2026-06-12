---
title: "Configuring PCMCIA"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by brn on 2006-09-12
I have a Dell Latitude CPx laptop running Dapper, using a 56 KB PC Card modem that I must configure each time I start the computer.  I discovered that "cardmgr" does this but only when I run it from the command line (sudo).  Cardmgr reels off a list of error messages: > cardmgr[9207]: could not adjust resource: IO ports 0x100-0x3af: Function not implemented etc. but says nothing about correctly identifying and installing the modem.

The man page for cardmgr seems to imply that it runs automatically whenever a card is inserted or removed but this does not seem to be the case. The man page also states that >  Current card and device information for each socket is recorded in /var/lib/pcmcia/stab. but this file does not exist.  Its a minor inconvenience, but how can I get cardmgr to run at startup or whenever the card is inserted or removed, as described in the man page, without the error messages which I think apply to vacant card sockets.

---

### Post by 3rr0r on 2006-09-12
Not sure if what you are talking about is a program to auto start running, but I think you should check out System > Admin > Session Manager.  There should be a tab to show what programs start up, and a place to add them.  It might be Preferences in stead of Admin, I'm not at home to check it myself right now.  Hope this helps.

---

### Post by brn on 2006-09-12
Thanks for your reply 3rrr0r.  I tried session manager but it didn't work.  Digging around I found /etc/pcmcia/config.opts which held all the port and memory references that cardmgr reported as errors.  I commented each of these and restarted.  This  time cardmgr failed completely.  So I reinstated them and once again it works.  But only from the command line.  Here are some of the things I see but don't understand:

 [LIST]
[*]All else being equal, /dev/modem does not exist.
[*] When I invoke cardmgr, /dev/modem is created, linked to ttyS1.
[*] When I hibernate the computer, /dev/modem continues to exist. 
[*] But the modem card is inaccessible.  I must run cardmgr again.
[*] When I shut down completely, /dev/modem disappears.
[/LIST]
I am bewildered.

---

