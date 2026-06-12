---
title: "Using SSH or Telnet through..."
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-12-07
Hey all!

I'm running a wireless a router (DI-624) on my XP machine, and ubuntu on my laptop, i was just wonderin how get SSH or Telnet working...

I have putty on my desktop and my ifconfig is:

```
adduds@adtop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:12:F0:6E:79:34
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe6e:7934/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3995062 (3.8 MiB)  TX bytes:5219030 (4.9 MiB)
          Interrupt:17 Base address:0xe000 Memory:e0208000-e0208fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2337810 (2.2 MiB)  TX bytes:2337810 (2.2 MiB)

```

Thanks in advance for any advice when I type (192.168.0.105) in SSH or Telnet in putty it times out...

1. is their something in ubuntu that i have to configure to get it to work?

---

### Post by Joe_CoT on 2005-12-07
you have to actually set up sshd on the ubuntu server for it to work

[SSH server how-to](http://ubuntuguide.org/#sshserver)

---

### Post by Grey on 2005-12-07
Have you installed openssh-server?

```
sudo apt-get install openssh-server
```

It doesn't come installed by default, so you do need to install it.  Other than that... I might think that perhaps a firewall on one of your machines might be blocking the request?

what happens when you ping your laptop?

```
ping 192.168.0.105
```

---

### Post by lleb on 2005-12-07
are you trying to say that sshd is not part of the default install of ubuntu?

ehh gahd that is horrid...  if you still have fits, make sure that iptables (firewall) is alowing connections on port 22.

---

### Post by quietglow on 2005-12-07
[QUOTE=lleb]are you trying to say that sshd is not part of the default install of ubuntu?

ehh gahd that is horrid...  if you still have fits, make sure that iptables (firewall) is alowing connections on port 22.[/QUOTE]

I think the idea is "one less open port" which is a pretty sound idea. "sudo apt-get install ssh" takes care of it. Note that if you're ssh'ing out of gnome, there is a very snazzy feature built into nautilis: just go Places>connect to server and select "ssh" from the available protocols. You get nice nautilis browsing a la OSX.

---

### Post by adduds on 2005-12-07
[QUOTE=Grey]Have you installed openssh-server?[/QUOTE]
Yes sudo apt-get install ssh

> 
what happens when you ping your laptop?


```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Adam Toews>ping 192.168.0.105

Pinging 192.168.0.105 with 32 bytes of data:

Reply from 192.168.0.105: bytes=32 time=2370ms TTL=64
Reply from 192.168.0.105: bytes=32 time=2ms TTL=64
Reply from 192.168.0.105: bytes=32 time=4ms TTL=64
Reply from 192.168.0.105: bytes=32 time=2ms TTL=64

Ping statistics for 192.168.0.105:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 2ms, Maximum = 2370ms, Average = 594ms

C:\Documents and Settings\Adam Toews>
```

---

### Post by lleb on 2005-12-08
[QUOTE=Grey]Have you installed openssh-server?

```
sudo apt-get install openssh-server
```

It doesn't come installed by default, so you do need to install it.  Other than that... I might think that perhaps a firewall on one of your machines might be blocking the request?

what happens when you ping your laptop?

```
ping 192.168.0.105
```[/QUOTE]

just because you can ping it, does not mean the firewall is not blockign port 22.

---

### Post by patrick295767 on 2005-12-08
(please avoid any use of telnet 'cos it's very un-secured connection)

---

### Post by Mr. Electric Wizard on 2005-12-08
All I had to do literally is apt-get install ssh, then on my XP box open up putty and log in.
Easy as pie.
SSH is the one thing i LOVE about linux.:p

---

### Post by adduds on 2005-12-08
Can you give me an example of how you logged on? lol, sorry to be lame, i'd like to get ssh to work cause i'd be able to use it from university and ish it'd be nice

---

### Post by Brunellus on 2005-12-08
$ ssh $HOST

where $HOST is replaced by the IP address of the host to which you wish to connect.  

to ssh to a computer behind a router, you must have your router forward port 22 to the host you want to ssh to.  Then, you ssh to the host's public IP--the router.

I do this to ssh to my box from the office.  great fun.

---

### Post by Mr. Electric Wizard on 2005-12-08
Or in my case, to log in to a Ubuntu box (or any linux box) from my WinXP box, I fire up Putty, and hit connect.
It fires up a new window with a Prompt.  That prompt is the terminal of the Ubuntu box.
You can do any command line stuff you need to do.  That includes apt-get update, etc.
Really cool feature!
Also, an even cooler feature is SCP.  You can fire up WinSCP and log into the Ubuntu box, and transfer files to and from it, just like you would in any FTP program...:cool:

---

### Post by Brunellus on 2005-12-08
hang on, what port does SCP use?

---

### Post by adduds on 2005-12-08
[QUOTE=Brunellus]

to ssh to a computer behind a router, you must have your router forward port 22 to the host you want to ssh to.  Then, you ssh to the host's public IP--the router.
[/QUOTE]

How do you forward port 22....sorry i don't know how


so when i'm in putty it asks me for the ip i would like to connect to so i type

192.168.0.106 (my ubuntu box IP)

the putty terminal or cmd opens sits their for a while:

[[IMG]http://img404.imageshack.us/img404/3982/puttyscreen19ni.th.png[/IMG]](http://img404.imageshack.us/my.php?image=puttyscreen19ni.png)

and then:

[[IMG]http://img404.imageshack.us/img404/2279/puttyscreenfail1kk.th.png[/IMG]](http://img404.imageshack.us/my.php?image=puttyscreenfail1kk.png)

The same thing happens when both firewalls are dropped (cept it doesn't prompt for the network access) only second window occurs

[quote=Brunellus]
I do this to ssh to my box from the office.  great fun.
[/quote]

Ya that's similar to the reason i want to, for university :)

---

### Post by Jaygo333 on 2005-12-29
This is completely off topic but one question about ssh, How do you change the port ssh uses from 22 to something else?

:arrow:h34r: Jaygo333 :arrow:h34r:

---

### Post by Suger on 2005-12-30
well, you type

ssh user@box

It asks for

password

and you're in, if :

1 - Your local box allows outbound connexions on port 22
2 - Your local box has a ssh client
3 - Your remote box has a ssh-server installed
4 - The router of your remote box routes port 22 to the said remote box.
5 - iptables on the remote box allows a connection on port 22
6 - you have an account on the remote box

It is possible to overcome 1, but the other 5 are necessary (well, not the 4 if the remote box is not behind a router, of course).

---

### Post by Chipmunk on 2005-12-30
adduds, It sounds like sshd may not be running, have you tried ```
ssh localhost
``` on your ubuntu box? This should get you a login if the server's running. This might help you track down if it's a case of sshd not running, or a network problem. Unfortunately I can't remember the way I installed sshd on mine #-o. But I *think* it was ```
sudo apt-get install sshd
```
I have now forwarded port 22 through the router (on port 2222 just 'cause I can) and was able to login from a friend's house last night using PuTTY.
You can check if sshd is running with a ps-A.

---

