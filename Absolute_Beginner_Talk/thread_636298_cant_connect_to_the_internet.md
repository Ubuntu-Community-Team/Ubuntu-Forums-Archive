---
title: "cant connect to the internet"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by tiggerthecharles on 2007-12-09
help please i cant connect to the internet.first i installed  ubuntu ok then i was told that i needed to have the connection when i installed it so i did it all over again but still i cant connect. what can i do?

---

### Post by p_quarles on 2007-12-09
You'll need to provide more details:
1) What kind of internet connection are you using? Wired? Wireless? Dialup?

2) If you are using a wireless card or a dial-up modem, what kind? If you're not sure, someone can help you find out.

---

### Post by MethodOne on 2007-12-09
If you're using dial-up, what ISP are you using?  Some ISPs, such as NetZero and PeoplePC in the U.S., require you to use their special dialers, which only work in Windows.   Also, some "acceleration" software, provided by your ISP or a third party, also won't work with Linux.

---

### Post by tiggerthecharles on 2007-12-15
alright it is wired dsl its ATT I have a modem its a speadstream modem

---

### Post by the Didey on 2007-12-15
this thread can probably get you there.

[http://ubuntuforums.org/showthread.php?t=603154&highlight=turn+off+roaming]("http://ubuntuforums.org/showthread.php?t=603154&highlight=turn+off+roaming")

---

### Post by Bartender on 2007-12-15
And you don't need to be connected to install.  I've installed dozens of times without an internet connection.  Just blow thru that part by clicking on "Cancel" or "Continue" or whatever.  You can always revisit the subject after installation.
DSL oughta be pretty easy unless the modem isn't compatible.  If you get to the point where it appears to be working with the modem but you get horrible connections check out disabling IPV6.  Either google it or do a search here.

---

### Post by p_quarles on 2007-12-15
@tiggerthecharles: My chat client didn't save our conversation in history, so I'm afraid I'm gonna have to ask for the same information again. Sorry. ;)

So, if you could, please paste the output of these two commands:
```
ifconfig -a
```
and 
```
cat /etc/network/interfaces
```

---

### Post by tiggerthecharles on 2007-12-16
for ifconfig -a 
Link encap: Ethernet HWaddr 00:1A:4D:3A:F1:65
Inet addr:169.254.7.32 Bcast:169:254.255.255 mask 255.255.0.0
Rx packets: 65 errors:0 dropped:0 overruns:0 frame:0
Rx packets:88 errors:0 dropped:0 overruns:0 Carrier:0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Iterrupt: 21 Base addres: 0xa000

---

### Post by schmildo on 2007-12-16
The "169.254.7.32" ip address indicates that your computer is setup to use DHCP but cannot find the DHCP server, (often this is the router).

You might be able to put your router's IP address into your browser and enable dhcp, or define your ubuntu's IP settings staticly.

... 
You need to find out what your router's IP address is. There are a few ways of doing it.

---

### Post by tiggerthecharles on 2007-12-17
and for the cat /etc/network/interface


auto lo
inface lo inet loopback


auro dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up# tine maintained by pppoeconf
provider dsl-provider

---

### Post by p_quarles on 2007-12-17
Okay, I think I see what happened. Did you attempt to manually configure your network at some point? That's what it looks like to me, but let me know if that's not the case, please.

If that is the case, here's how I would try to fix it. First, make a backup copy of your current interfaces file, for future reference:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
Now, edit the original file:
```
gksudo gedit /etc/network/interfaces
```
Delete the four lines at the bottom. Replace them with the standard configuration for a DHCP connection, as shown below:
```
auto eth0
iface eth0 inet dhcp
```
Save the file. You probably don't need to restart your computer to test this, just run the following:
```
sudo /etc/init.d/networking restart
```
If that doesn't work, though, do restart the computer. Ethernet cards sometimes come with weird settings that would make this necessary.

If that doesn't work -- well, I'll try to think of something else.

---

