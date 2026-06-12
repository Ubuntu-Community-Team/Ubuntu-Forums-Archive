---
title: "Help please!!!"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2006-07-24
Well i was using ubuntu  remote desktop connections..and it worked..
I just typed the xxx.xxx.xxx.xx
and connected to a server..


Now I m using Kubuntu and after I type the address on the Remote desktop connection field..the connect button is still unavailable!!!

Any ideas??  I alreadu doubled checked the ip address.

---

### Post by gigaferz on 2006-07-24
Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Creating link /root/socket-ubuntu.
Created link from "/root/socket-ubuntu" to "/tmp/ksocket-root"
/usr/bin/iceauth:  creating new authority file /root/.ICEauthority
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Creating link /root/tmp-ubuntu.
Created link from "/root/tmp-ubuntu" to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0
DCOP aborting call from 'anonymous-7485' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
ScimInputContextPlugin()
~ScimInputContextPlugin()



I tried sudo krdc..

well..I guess its more complicated....  It worked at my house with ubuntu...

---

### Post by gigaferz on 2006-07-24
cool ..

Guess what in kubuntu you need to type rpd:/xxx.xxx.xxx.xx

and before that you need to install rdesktop using sudo apt get install,...

wow!!!

---

