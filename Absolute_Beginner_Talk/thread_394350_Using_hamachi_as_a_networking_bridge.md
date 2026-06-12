---
title: "Using hamachi as a networking bridge"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Zaen on 2007-03-26
Hi everyone,
I have question(s) involving Hamachi. I successfully installed hamachi onto a computer running ubuntu 6.06, and got everything set up. A friend was able to logon, but when he hosted a network game , I couldn't see it ( I was trying to play on a different computer, but I'm on the same network as the hamachi server). 

So my questions are as follows:  
1 Does hamachi act as a network bridge (i.e., my friend is now a part of my local area network) or do I have to logon/ set it up as a bridge 

2 What do I have to do to configure it to be a network bridge rather than a host?

3 What security measures I can take to make it a more secure network bridge? I don't currently have a firewall installed on that pc, but there is an NAT firewall between the dsl router and the rest of the network.

any feedback is appreciated
Thanks,
Zaen

---

### Post by sin on 2007-04-30
It tries to be a VPN but it has issues.

If you want to play LAN games on it, you can change your localhost to the hamachi ip instead of 127.0.0.1 in /etc/hosts, but that's not a very nice solution. 

I'd also like some more insight on this.

---

### Post by fakie_flip on 2007-06-30
I cant get ghamachi to work. The dot near people's names stay red. We don't have software firewalls, so I don't know why this is happening except that the linux client may be buggy.

---

### Post by fakie_flip on 2007-07-15
Solved: I needed to run tunfg as root.

---

### Post by samsercher on 2007-10-16
> **fakie_flip said:**
> Solved: I needed to run tunfg as root.

I have been having the same problems with hamachi. Could you please explain what tunfg is. I try to look for man pages and searched google and tunfg does not seem the exist. Thanks in advance for any help.

---

### Post by dlr365 on 2007-10-17
> **samsercher said:**
> I have been having the same problems with hamachi. Could you please explain what tunfg is. I try to look for man pages and searched google and tunfg does not seem the exist. Thanks in advance for any help.

The command that you need to run as root is **tuncfg** (with a c).  This sets up the tunnel device that Hamachi uses.  Then you need to run **hamachi-init** as the user you wish to use Hamachi with.  This will create the Hamachi settings file in your home directory.

After that you can run **hamachi start** to start Hamachi.  See the readme file that came with Hamachi for the other commands for joining networks, etc...

---

### Post by lazyart on 2007-10-18
go to [www.penguinbyte.com](www.penguinbyte.com) and get ghamachi.  It's a graphical front-end for Hamachi on linux.  When you launch it, it will detect if you have neglected to start tuncfg and allow you to enter the sudo password to get it started.

I have it installed on my laptop, my desktop and my Windows server.  Nice to be able to access files from whereever you may be.

---

