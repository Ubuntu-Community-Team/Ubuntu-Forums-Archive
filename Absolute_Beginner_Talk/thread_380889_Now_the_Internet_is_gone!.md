---
title: "Now the Internet is gone!"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Cilionelle on 2007-03-10
Hi!  After fiddling around trying to get some help adjusting the screen resolution (stuck at 640x480) my internet connection has dropped from the laptop I'm using.  I am running it via ethernet cable through the router (NetComm NB5540) to the modem (D-Link DSL-502T).  It has connected before, but now... not.  I would like to get the updates I need to continue to use (ha!) Ubuntu, but need some help.

(Is it called "Linux for Human Beings" because it's so difficult to work with?)

---

### Post by Obor on 2007-03-10
if your connection is eth0 then you could try
```
sudo ifup eth0
``` in terminal

---

### Post by al1b1 on 2007-03-10
Im using a wireless card and my internet is really tempermental too. I find that doing a cmplete restart, replugging in the card and filling out all the information out again in network manager sometimes works.

---

### Post by oilchangeguy on 2007-03-10
playing with screen resolution should not affect your internet connection. have you paid attention to your modems lights?

---

### Post by Cilionelle on 2007-03-10
Well, considering the connection is fine in Windows (via the same router and modem) but on a different computer (fortunately), I figure it's an Ubuntu thing.

The message that I get after the "ifup" command is: "ifup: interface eth0 already configured"

I can also "ping" the router from the terminal successfully.

---

### Post by PoppaSteve on 2007-03-10
I'm VERY new to Ubuntu, and I'm not at my Ubuntu machine, but where you see if your ethernet connection is enabled, look at the DNS setting.

What happens to me is that my router's address is the first one listed, so that my router is trying to connect to the internet through itself.  Well, that ain't gonna work!

I delete the first address, then start Firefox and it works.  See if that doesn't help.

Now if I could find a way for the router to not look for itself when I boot.

---

### Post by Cilionelle on 2007-03-10
My router's IP is not listed under the DNS Servers tab.  There is only one entry, a 10.1.1.1 and that's it.

---

### Post by PoppaSteve on 2007-03-10
That's what worked for me.

Good luck on your problem.

---

### Post by Obor on 2007-03-10
what is the result of
```
ifconfig
```
and what is in your /etc/network/interfaces file? ```
gedit /etc/network/interfaces
```

---

### Post by Cilionelle on 2007-03-10
From "ifconfig":

eth0     Link encap:Ethernet   HWaddr 00:0D:56:38:01:46
     inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
     inet6 addr: fe80::20d:56ff:fe38:146/64 Scope:Link
     UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
     RX packets:22 errors:0 dropped:0 overruns:0 frames:0
     TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:2126 (2.0 KiB)  TX bytes:6560 (6.4 KiB)
     Interrupt:7

From "gedit [etc]":

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface eth0 inet dhcp


auto wlan0
iface wlan0 inet dhcp

Now what?

---

### Post by Obor on 2007-03-10
go to administration - networking - wired connection - properties - it should say Automatic configuration DHCP (and enable this connection)

if that doesn't help maybe try changing the /etc/network/interfaces to 
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by Cilionelle on 2007-03-10
Now when I open Firefox, instead of Google timing out, there is no connection at all.  Tried both the suggestions, but to no avail.  Any other ideas?

---

### Post by Obor on 2007-03-10
try restarting the connection. 
```
 sudo ifdown eth0 && sudo ifup eth0
```
if that doesn't work then I have no idea but I'm sure someone else will.

---

### Post by Cilionelle on 2007-03-10
Thanks for the help, Obor, but it's still not working properly.  It is sending stuff, but nothing but the smallest amt is getting back through.  Maybe it's got a cold or something.  Oh well, I'll have to try tomorrow!  Ta!

---

### Post by Jaidee on 2007-03-10
Did you try to enter your router's IP in your DNS settings? If you can ping your router, I would say this is a DNS issue. Please add 192.168.1.1 to the DNS settings.

---

### Post by freebird54 on 2007-03-10
I'm not on my Ubuntu box - so I can't steer you exactly (old Win95 laptop!) BUT I suspect that you are running into the ipv6 problem.  If you search the forums on ipv6 you will find several ways of disabling it - which could lead to immediat e improvement.  You can also config Firefox to stop trying to use ipv6 by putting about:config in the address bar and searching for ipv6 - set (dbl-click) the disable option to TRUE and try that.

Hope it helps

---

### Post by Cilionelle on 2007-03-10
Right.  I'v disabled IPv6 for Firefox, and the Internet is back.  However, I am still unable to download updates and stuff.  The connection is not getting through.

"W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc_2.4-lubuntu12.3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc_2.4-lubuntu12.3_i386.deb)
  Could not connect to 192.168.1.1:8080 (192.168.1.1). - conntect (111 Connection refused)"

and so on with all the other packages I've elected to download.  Any ideas?

---

### Post by Cilionelle on 2007-03-10
still wondering if anyone can help me?

---

### Post by freebird54 on 2007-03-11
Hi, I'm back on my Ubuntu machine.  Here are the rest of the 'fixes' that worked for me...

```
gksudo gedit /etc/modprobe.d/blacklist
```

and add

```
blacklist ipv6 

```
Save the file and reboot your computer. Is the net any quicker?

If you want to hammer the problem more ways you could try

```
gksudo gedit /etc/modprobe.d/aliases

```
and comment out the entry as shown (# is the comment marker)

```
alias net-pf-10 ipv6

```
making it:

```
#alias net-pf-10 ipv6

```

and then add these lines (without extra spaces or changes)

```
alias net-pf-10 ipv6 off 
alias net-pf-10 off 
alias ipv6 off 
```

Again, save the file, and reboot to be sure it is picked up by the system.

Between those 2 you should be back at full speed.  Actually - the first one should work by itself  :)

---

