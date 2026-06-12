---
title: "Networking Ubuntu 6.10"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-04-29
I am getting frustrated.
I can go into System, Networking Tools, enter the IP address of my router and ping it, another WinComputer connected via USB Wireless adapter to that same router and ping it, or, I can ping my own computer.

What is a little strange to me is that my own machine is represented by an IP address totally foreign to me:

it's an address that starts with 127. when all the address I know about from networking in XP start with 192.

If I poke around and experiment with settings, I can ignorantly manage to get computers in my MSHOME network to show up under Places-Networks.

Once, I even succeeded in getting Samba to display and mount those machines, actually succeeded in opening several photo files residing on a remote machine to open in Photoshop 7 using crossover.

But, if I reboot my machine, it's start over time - nothing comes back the same.

Right now, I can only get my router and MSHOME to show up under Places, Network.  Double clicking the router brings up an error message, double clicking on MSHOME brings up an icon that represents my machine.  Double clicking on that icon brings up an icon "My Files".  And double clicking on the "My Files" icon brings up a dialog informing me that I have to "sign-in" as a guest to view the contents.  Signing in is never successful (I only use one password on this machine - so, I don't understand what is happening here).

I have the bookmark for the one blissfully successful session I've experienced in Samba stored.  If I click on it in Samba, the share will briefly appear in the share pane on the right side of the dialog box, but, disappears almost immediately.

I am growing weary of the sound of broken glass.

I know the share name is valid - it once worked for me.

I like tinkering as much as the next guy (or I wouldn't be messing around with ubuntu), but, the lack of consistency is starting to grind me down.

It cannot possibly be this difficult.

Can someone help me?

Thanks!

Caruso

---

### Post by mendingo84 on 2007-04-29
If you are talking about 127.0.0.1 that is loopback...localhost. You should set your IP address to smth lile 192.168.x.x . Maybe that's what's bothering it

---

### Post by louieb on 2007-04-29
To see you network IP
Applications>Accessories>Terminal> **ifconfig**
If you have internet access you will see the 192... address listed.

Samba is what it is. I wish it were easier too. I think the sign on it wants is for a user on the remote machine. 
What I've found. [LIST]
[*]Linux machine to Linux machine:  easy  (several ways ssh, ftp,nfs)
[*]XP machine to XP machine: easy (setup a work group)
[*]Linux machine to XP machine:  pain in the as:confused:
[*]Vista machine to anything:  pain in the as:confused: (impossible if you have Norton Internet security installed)[/LIST]I'm not much help with Samba I just stumbled around and don't know how I got the shares to work. If I run across a good Samba guide I'll pass it on.

---

### Post by carusoswi on 2007-04-29
The result of ifconfig:

th0      Link encap:Ethernet  HWaddr 00:30:1B:B4:E8:58  
          inet addr:169.254.241.67  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::230:1bff:feb4:e858/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21595 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18996 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16617268 (15.8 MiB)  TX bytes:2353794 (2.2 MiB)
          Interrupt:209 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:773 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70349 (68.7 KiB)  TX bytes:70349 (68.7 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.57.1  Bcast:192.168.57.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.115.1  Bcast:172.16.115.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


I have internet access (am using it now).  Obviously, it isn't showing up as it should.  Also, in Samba, how do I reset the host ip to a 192 address.  I don't see how or where I do that?

Thanks for pointing me in the right direction.

Caruso

---

### Post by carusoswi on 2007-04-29
I finally just gave up on Ubuntu 6.10 and networking.  Had been trying to upgrade to 7.04 for a week or so without luck.  The install kept sticking with a fetch (or make that can't fetch) error.  I had no problem, however, downloading the disk image.  So, I just now installed 7.04 fresh as a third operating system on my computer.  Took me 10 minutes to search out how to resolve my ATI graphics resolution issue - I did that before trying anything else.

Without even downloading Samba, I just clicked on places, networks, and there is my entire network.  Click on another computer and all its shared resources are there for me to poke around in.

Now, I need to see about getting Crossover installed along with the few aps from Winxp pro that I truly need.

Still don't know what was wrong with 6.10, but it was probably something I did while messing around that only a new install would correct.

Perhaps 7.04 is just a better networker as well.

Thanks again for the replies.

Caruso

---

