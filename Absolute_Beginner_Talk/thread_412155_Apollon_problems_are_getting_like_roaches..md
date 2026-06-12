---
title: "Apollon problems are getting like roaches."
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Irmis on 2007-04-17
I start Apollon it returns this:
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-irmis"
Link points to "/tmp/kde-irmis"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
irmis@Irmis:~$ X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Launched ok, pid = 23460
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3e00b56
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3e00b56
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x3e00b56

Then opens with one network (Ares) connected, that stuff looks bad to me.:confused:

---

### Post by jordanmthomas on 2007-04-17
I know it seems unlikely, but most of those errors are from Ubuntu putting things in your xorg.conf that probably don't belong.  

It always seems to put in sections for wacom and stylus stuff, which is for tablet pcs.  Once you get rid of all the stuff with wacom from your xorg.conf, most of those errors will go away and you can focus on what the real error is.

---

