---
title: "Azureus Trouble"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by StormGuy on 2007-11-25
I recently installed Azureus and attempted to use it for torrenting files.  Initially, I set Azureus so that it would encrypt my torrents.  However, any time I tried to load a torrent file for download, it crashed.  So, I tried unselecting the "encrypt" option, and now Azureus crashes immediately.  I ran it in the terminal and got the following error:

```
[alert] Alert:3:UPnP: Mapping 'Incoming Peer Data Port (TCP/40983)' failed
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b2012c52e11, pid=8168, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/opus/.azureus/hs_err_pid8168.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

I tried a fix that I found for general Azureus problems that involved downloading the new .jar file and renaming it to Azureus2.jar.  Unfortunately, it didn't help.

I'm unfamiliar with Java and Azureus, so I'm not sure how to read the error.  Has anybody here had more experience with both and could suggest a solution?

Thanks.

---

### Post by Pumalite on 2007-11-25
Try ktorremt. It's better. It's in the repos (through Synaptic)

---

### Post by Ub1476 on 2007-11-25
I would suggest [**Deluge**]("http://deluge-torrent.org/News:Portal") (repos), which is less resource heavy and still has the same features as Azurues (+ it has plugins).

But if you want to stick with Azureus, I can't help you there.

---

### Post by Dapilot1 on 2007-11-25
I could not get Azureus to work either. I removed it and installed Deluge from Add/Remove and it has worked fine for me.

---

### Post by bluepowder7 on 2007-11-25
did someone say Deluge?  :D

---

### Post by StormGuy on 2007-11-25
Deluge seems to be working fine.  Thanks for the suggestion :D

---

