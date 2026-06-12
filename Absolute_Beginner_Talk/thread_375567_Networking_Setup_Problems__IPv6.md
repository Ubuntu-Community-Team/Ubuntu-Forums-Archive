---
title: "Networking Setup Problems : IPv6?"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Iesu on 2007-03-03
I have posted twice on this problem in other threads but as it wasn't the threads' main focus I didn't get the answers I need, and the more I use Ubuntu, the more it is bugging me.
I should first clarify that I'm using Kubuntu, but that has no bearing on the problems I'm experiencing. My problem is that my internet connection works most of the time, but not with aptitude or wget, unless I ping the address I want to DL from first.
I have come to Ubuntu from openSUSE, so I knew I had to disable IPv6 in Firefox to get it working, and promptly did that after I installed. After researching this problem extensively I have heard a number of people blame it on IPv6 and also on their DHCP setup. I have tried both editing the /etc/modprobe.d/alias to include th following lines:
alias net-pf-10 ipv6 off
alias net-pf-10 off 
alias ipv6 off
(I was unsure how the file worked and this seemed to be the most sure-fire way of disabling the problem protocols), and also tried my networking settings on direct connection to the internet and automatically aquire proxy settings.
I also saw someone mention editting their /etc/apt.conf file. This file is not present on my system, but doing so only seemed to be changing the proxy settings.
Any help here would be greatly appreciated as pinging my repos is getting exceptionally tedious.

---

### Post by tgalati4 on 2007-03-03
Add the line:

blacklist ipv6

to /etc/modprobe.d/blacklist

reboot

---

### Post by Iesu on 2007-03-03
Ok, so I blacklisted IPv6 and the problem still exists. So if IPv6 isn't the problem, what else could cause ping to work but not aptitude and wget without ping's assistance?

---

### Post by tgalati4 on 2007-03-04
I presume that you rebooted after blacklisting ipv6.

I presume your /etc/hosts file contains the following:

127.0.0.1 localhost
127.0.1.1 yourhostname

(any other local hostnames like printers and local machines with fixed IP's)

Also, post the output of:

route

---

### Post by Iesu on 2007-03-05
Thank you so much tgalati4 for you continued support.
I did indeed reboot after I blacklisted ipv6
And my hosts file looks exactly like the lines you typed. My setup is this one machine connected directly to my DSL-G604T router. No other printers or machines connect to the router except an occasional wireless connection. I checked the problem before placing this post and it definately still exists. Here is my output from route:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.0.0.0       U     0      0        0 eth1
default         mygateway1.ar7  0.0.0.0         UG    0      0        0 eth1

I didn't think formatting that was really necessary.  Thanks again.

---

### Post by Iesu on 2007-03-05
SOLVED! I simply had to manually specify my DNS servers in /etc/dhcp3/dhclient.conf as described in [this]("http://www.ubuntuforums.org/showthread.php?t=358749") post. I think the actual solution is the 8th post. Huge thanks to tgalati4 and mrmonday for their help....anyone know how I flag this thing as resolved?

---

