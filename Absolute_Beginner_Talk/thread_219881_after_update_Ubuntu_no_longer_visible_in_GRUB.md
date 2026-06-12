---
title: "after update Ubuntu no longer visible in GRUB"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Alain1 on 2006-07-20
I installed Kubuntu in dualboot. (also XP)
After update I can not longer see the opportunnity to choose for Ubuntu in the GRUB.
I can only start up Windows XP.
Can someone help me to choose for Kubuntu again?
I'm not longer able to give some output from the Terminal because I can not start it
Tx:)

---

### Post by shoot2kill on 2006-07-20
have you got the live cd,,, try booting to that and try and post your menu.lst from boot/grub/

---

### Post by Alain1 on 2006-07-20
I did the following after inserting the Live-CD : remember I'm a very newbie ;) 

ubuntu@ubuntu:~$ sudo mkdir /media/linux
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda6 /media/linux
ubuntu@ubuntu:~$ sudo kwrite /media/linux/boot/grub/menu.lst
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
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

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Creating link /root/cache-ubuntu.
Created link from "/root/cache-ubuntu" to "/var/tmp/kdecache-root"
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_ubuntu__0
and start dcopserver again.
---------------------------------

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
KCrash: Application 'kwrite' crashing...
Warning: connect() failed: : No such file or directory
KCrash cannot reach kdeinit, launching directly.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

drkonqi: cannot connect to X server :0.0
ubuntu@ubuntu:~$

---

### Post by Alain1 on 2006-07-20
My problem is solved ! I did the following :

sudo mkdir /media/linux
sudo mount -t ext3 /dev/hda6 /media/linux
sudo mv /media/linux/boot/grub/menu.lst /media/linux/boot/grub/menu.rm
sudo nano /media/linux/boot/grub/menu.lst

and now i can reboot
thanks everyone:D :D :mrgreen:

---

