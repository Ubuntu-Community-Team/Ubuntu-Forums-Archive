---
title: "How to post logs."
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by grimmson on 2005-09-29
This is funny. I've used computers for ten years now and I hate asking super simple questions but I've got a boot up dirver problem (I think). How can I post those two logs everyone wants to see to help people troubleshoot issues with the fancy scrole bar. Since were on the subject what are the names and directorys of those logs? /etc/x11/xorg.0.log? The moral of the story is when you exaust google you learn to post properly.

---

### Post by az on 2005-09-29
[QUOTE=grimmson]This is funny. I've used computers for ten years now and I hate asking super simple questions but I've got a boot up dirver problem (I think). How can I post those two logs everyone wants to see to help people troubleshoot issues with the fancy scrole bar. Since were on the subject what are the names and directorys of those logs? /etc/x11/xorg.0.log? The moral of the story is when you exaust google you learn to post properly.[/QUOTE]

dmesg |less

or 

cat /var/log/messages

Look in /var/log for all the logs.

---

### Post by lao_V on 2005-09-29
[quote=grimmson]This is funny. I've used computers for ten years now and I hate asking super simple questions but I've got a boot up dirver problem (I think). How can I post those two logs everyone wants to see to help people troubleshoot issues with the fancy scrole bar. Since were on the subject what are the names and directorys of those logs? /etc/x11/xorg.0.log? The moral of the story is when you exaust google you learn to post properly.[/quote]

Have you tried booting from a LiveCD and (mounting the drive if necessary) posting the log that way?

---

### Post by grimmson on 2005-09-29
Talk a bout a timely response. You can't get a pizza this fast. I guess my next questions pertain to what logs to post. I have a ppc (mac) with a ati7000. Install went fine, boots fine to just b 4 the login screen. I get a black screen, circle, arrow (mouse) and It doesn't post loging screen (like it should.) I work around this by hitting ctrl,alt f1. I can then log into terminal or hit f7 and see the graphical login. I assume but hitting ctrl,alt f1 at the right time I interupt the boot process b 4 the error (may require several reboots to time it right.) Any thoughts are appriciated.


dmesg |less (<-- typed dmesg |less and don't have a fancy scrolling window for logs)

---

### Post by grimmson on 2005-09-29
tried dmsg |less got this

pcilynx0: SelfID packet 0x568c7f80 rcvd
ieee1394: SelfIDs failed monotony check with 22/0
ieee1394: Error in SelfID stage, resetting
pcilynx0: resetting bus (long bus reset) on request
pcilynx0: bus reset interrupt
pcilynx0: SelfID process finished (phyid 0, root)
pcilynx0: SelfID packet 0x568c7f80 rcvd
ieee1394: SelfIDs failed monotony check with 22/0
ieee1394: Stopping out-of-control reset loop
ieee1394: Warning - topology map and speed map will not be valid
usb 1-2: new full speed USB device using ohci_hcd and address 2
hub 1-2:1.0: USB hub found
hub 1-2:1.0: 4 ports detected
pcilynx0: invalid transaction code
ieee1394: got invalid ack 254 from node 65535 (tcode 4)
ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
pcilynx0: resetting bus (long bus reset, force_root set) on request
pcilynx0: bus reset interrupt
pcilynx0: SelfID process finished (phyid 0, root)
pcilynx0: SelfID packet 0x568c7f80 rcvd
ieee1394: SelfIDs failed monotony check with 22/0
ieee1394: Error in SelfID stage, resetting
pcilynx0: resetting bus (long bus reset) on request
pcilynx0: bus reset interrupt
pcilynx0: SelfID process finished (phyid 0, root)
pcilynx0: SelfID packet 0x568c7f80 rcvd
ieee1394: SelfIDs failed monotony check with 22/0
ieee1394: Error in SelfID stage, resetting
pcilynx0: resetting bus (long bus reset) on request
pcilynx0: bus reset interrupt
pcilynx0: SelfID process finished (phyid 0, root)
pcilynx0: SelfID packet 0x568c7f80 rcvd
ieee1394: SelfIDs failed monotony check with 22/0
ieee1394: Error in SelfID stage, resetting
pcilynx0: resetting bus (long bus reset) on request
pcilynx0: bus reset interrupt
pcilynx0: SelfID process finished (phyid 0, root)
pcilynx0: SelfID packet 0x568c7f80 rcvd
ieee1394: SelfIDs failed monotony check with 22/0
ieee1394: Error in SelfID stage, resetting
pcilynx0: resetting bus (long bus reset) on request


Does it mean anything to you? this is only a bit of it. Couldn't get it from start.

---

