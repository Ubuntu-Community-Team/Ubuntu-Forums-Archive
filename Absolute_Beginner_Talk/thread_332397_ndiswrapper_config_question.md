---
title: "ndiswrapper config question"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Mr.Bojangles on 2007-01-06
Okay, i am a bit stumpped right now. I'm a total newb so i could use some help i instaleld ndiswrapper, then installed my driver for BCM4306 wlan card it was a driver named bcmwl5.inf dunno if this right, then i checked my config wlconfig and my card is not showing up.. here's my temrinal output, any help on getting my wireless card up and running would be great.

> 
bojangles@bojangles-laptop:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 
bojangles@bojangles-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

bojangles@bojangles-laptop:~$ 


---

### Post by sjnovick on 2007-01-06
The likely culprit is the Broadcom wireless drivers that are now included in the Linux kernel.  Unfortunately the Broadcom drivers don't work.  So you need to remove them:

1.  Remove the driver from loaded modules
# rmmod bcm43xx
2.  Blacklist bcm43xx so that it doesn't get loaded upon reboot.  See the file /etc/modprobe.d/blacklist.  Add the entry

blacklist bcm43xx

3.  Now, load ndiswrapper:
# modprobe ndiswrapper
# depmod -a

4.  You should be able to eth1 in your network manager.  If you prefer the manual route:
# iwconfig eth1  [you may need to put info here like essid]
# ifconfig eth1 up
# dhclient eth1

That should do it.  If you do not have wireless upon reboot, add the word ndiswrapper to your /etc/modules file.

---

### Post by ubunturules on 2007-01-06
check out my howto [here]("http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306")

ubunturules

---

### Post by Mr.Bojangles on 2007-01-07
Okay, tried to rmmod the bcm43xx drivers didn't work:
> root@bojangles-laptop:/home/bojangles# rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules


---

