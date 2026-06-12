---
title: "network is unreachable"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by beamo on 2006-12-24
I reinstalled 6.06 and now I can't get an internet connection. I've reinstalled many times in the past and the internet connection was always working as soon as the install was finished so I don't understand what is going on. Eth0 is active and configured with DHCP enabled. I've tried deactivating/activating, using static ip address with the correct addresses I got from Windows which works without problems, and have searched through many, many threads on this forum all to no avail. When I try to ping my router it says "network is unreachable." This is driving me absolutely nuts because I have never had any problems like this in the past. Is there anything I am missing?

---

### Post by MkfIbK7a on 2006-12-24
try the third post down on this thread and page 


[http://www.ubuntuforums.org/showthread.php?t=133599&page=3](http://www.ubuntuforums.org/showthread.php?t=133599&page=3)

---

### Post by beamo on 2006-12-24
Thanks wert, I tried that and no luck. I'm thinking I must have scratched the install cd or something because I just installed 6.10 and it works fine...

---

### Post by MkfIbK7a on 2006-12-24
im glad at least 6.10 works for you :D

---

### Post by 2CV67 on 2006-12-25
DANGER - I am a newbie & don't understand much, but my symptoms were like yours & I found a cure as follows, quoting from long post at:
[http://www.ubuntuforums.org/showthread.php?t=318796&page=4](http://www.ubuntuforums.org/showthread.php?t=318796&page=4)

Quote:

[I]Again blindly following leads from French Ubuntu forum, I added "restricted" in a line of code as follows:
::::::::::::::::::::::::

sudo gedit /etc/network/interfaces

iface wlan0 inet dhcp
address 192.168.1.9
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid DW-B-200-3d555
wireless-key 260E***********

Change last line to:

wireless-key restricted 260E***********
::::::::::::::::::::::::::::::::::::::::

After which Ubuntu boots with Internet connection blazing![/I]

Unquote.

I have seen this trick elsewhere too.

At your own risk, but don't think it can do any harm.

---

