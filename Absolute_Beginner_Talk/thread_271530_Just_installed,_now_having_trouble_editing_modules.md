---
title: "Just installed, now having trouble editing modules and interfaces"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by hillrunr on 2006-10-04
OK, I now have installed Ubuntu on my old PC that couldn't even handle Windows anymore (thanks much for the help with that!). Now, I'm on to the next roadblock. My network card was not detected. I found in the Wiki that I'm supposed to add "3c509" to the /etc/modules file and edit the /etc/network/interfaces file.

So I browse to the modules file, open it up, and add 3c509 at the bottom of the file. One problem. The file owner is root and I don't have permissions to save. I can't seem to get around this. Given that the account I created during installation is the only account I have on Ubuntu right now, how do I grant myself the permissions needed to edit this file so I can get my network card working?

Thanks much for the help.

**Edit:** Now that I'm looking at the interfaces file, I'm confused again. What am I supposed to edit with this? The Wiki only tells me to edit the interfaces file, nothing about what I'm supposed to edit it with.

---

### Post by Sef on 2006-10-04
are you on dial up or broadband?

---

### Post by hillrunr on 2006-10-04
Broadband. Sorry, I should have referenced the Wiki article I found. I found [this article](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards?highlight=%28network%29%7C%28card%29) and my network card is the first 3Com model listed on there. The directions say:

> add 3c509 to /etc/modules, and edit /etc/network/interfaces

My issues are twofold: 1) The modules file is owned by root and I don't have permissions to edit the file and can't figure out how to get the permissions. 2) It says I'm supposed to edit the interfaces file but doesn't tell me anything about how to edit it or how to determine how to edit it.

---

### Post by Sef on 2006-10-04
you would have to use sudo for that access.

From RootSudo

> In Linux (and Unix in general), there is a superuser named root. The Windows analog of root is Administrator. The superuser can do anything and everything, and thus doing daily work as the superuser can be dangerous. You could type a command incorrectly and crash the system. Ideally, you run as a user that has only the privileges needed for the task at hand. In some cases, this is necessarily root, but most of the time it is a regular user.

By default, the root account is locked in Ubuntu. This means you cannot login as root or use su. Instead, the installer will setup sudo to allow the user that is created during install to run all administrative commands.

This means that in the terminal you can use sudo for commands that require root privileges. All programs in the menu will use a graphical sudo to prompt for a password. When sudo asks for a password, it needs YOUR USER Password; this means that a root password is not needed. 

---

### Post by hillrunr on 2006-10-05
So I just go to the terminal, type in sudo, then browse to and edit the file from the terminal? I can give that a shot this evening. I saw something referencing sudo when searching the forums but couldn't get it to work yesterday evening. I'll browse through the Wiki now that I know that's the answer and see what documentation I can find.

Sorry if I sound so clueless. Unfortunately, while I liked our Linux machines in school, since graduating, I've been thrust back into the world of Windows programming and I haven't touched a Linux machine in 6+ years. It's amazing how much you can forget in that time.

---

### Post by srt4play on 2006-10-05
Press Alt-F2 to get a run dialog.  type in the run dialog: 

gksudo gedit /etc/modules  

That will give you a graphical means of editing the file. 

We use sudo and gksudo to gain temporary root privileges to run system commands and edit system files among other things.

---

### Post by hillrunr on 2006-10-05
Thanks to both of you for your help! I also found a [RootSudo](https://help.ubuntu.com/community/RootSudo) document in the Wiki now that I knew what to search for and the combined learning leaves me confident that, if I can figure out what I need to do with the interfaces file, I'll be online quickly this evening from my Ubuntu desktop. If not, I'll probably have a follow-up question to post and I have no doubt I will again get useful responses quickly.

---

### Post by hillrunr on 2006-10-05
Still having trouble if someone could help me through this.

I added the following line to /etc/modules:
3c509

I found elsewhere to add the following to /etc/network/interfaces and did so:
auto eth0
iface eth0 inet dhcp

I also found elsewhere to run the following commands:
**sudo dhclient**
(Result: a bunch of "send_packet: Network is down" errors followed by "No DHCPOFFERS received." and "No working leases in persistent database - sleeping."

**sudo ifconfig -a**
(Result: I see the following for eth0)
Link encap:Ethernet  HWaddr 00:10:5A:25:99:45
BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
Interrupt:10 Base address:0x230

Rebooted and nothing.

Anyone have any thoughts?

---

### Post by srt4play on 2006-10-10
How about running the command 'lsmod' and see if 3c509 is in the output.

---

