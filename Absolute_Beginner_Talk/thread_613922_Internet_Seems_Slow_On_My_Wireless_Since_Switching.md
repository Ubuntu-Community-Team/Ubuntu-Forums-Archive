---
title: "Internet Seems Slow On My Wireless Since Switching To Ubuntu?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Tachions on 2007-11-15
hey it might be im sharing a t3 connection with a whole apartment complex and then sharing connection on our modded linksys router, BUT loading web pages and surfing is extrememly slow, whats going on?

any same situatons? any possible tweaks? let me know thanks

---

### Post by cubeist on 2007-11-15
when I tried GG my internet was also slow until I turned off IPV6...since I only use firefox the easiest way is type "about:config" in the address bar and then search for ipv6... then just double click the ipv6 option and it will turn it off... boom, instantly faster internet... for me anyway...

you can also search the forums for a tutorial to turn ipv6 off at the system level...

---

### Post by Tachions on 2007-11-15
what is ipv6?

is it important, or okay to turn off?

---

### Post by cubeist on 2007-11-15
ipv6 is the next standard for ip addresses on the web (because ipv4 is running out of numbers), but nobody uses ipv6...it is years away from being used mainstream... in my opinion it should be disabled by default.

Anyway, it is safe to turn off, and you can always turn it back on if you need it...

for much more info you can view the wikipedia ipv6 entry...

---

### Post by Tachions on 2007-11-15
hey thanks cubeist,

i havent seen too much of a difference, still takes bout 20 secs to load a new page, never had this problem in windows. dont know what it is. 

any other suggestions would be great! thanks a lot!

---

### Post by Tachions on 2007-11-15
bump

---

### Post by skymera on 2007-11-15
[www.opendns.com](www.opendns.com)

and this:

sudo gedit /etc/sysctl.conf

    * Then again, scroll to the bottom and just add these lines to it. 

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

---

### Post by Tachions on 2007-11-15
hey skymera 

what does inputing that code do? just wondering. i appreciate your help

---

### Post by cubeist on 2007-11-15
> **skymera said:**
> [www.opendns.com](www.opendns.com)



Switching to OpenDNS is likely not the best fix if you don't have access to the router... I tried OpenDNS once, and the change was hardly noticeable...


In regards to the problem, perhaps there is something in your interfaces file that is slowing things down.  Here is how to check: open a terminal and type "sudo gedit /etc/network/interfaces"  then enter your password, and a new window will open with your interfaces file.  In my experience, it is best to comment out everything but the loopback options, here is my file for reference:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#iface eth0 inet dhcp
#auto eth0

#iface wlan0 inet dhcp
#auto wlan0
```

It is also a good idea to backup files before editing them!

---

### Post by Tachions on 2007-11-18
bump

---

