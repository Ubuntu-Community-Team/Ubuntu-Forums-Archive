---
title: "how to open a certain port"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-10-15
I'm trying to use azureus but it seems that when I try testing port 6881 I get a NAT error.  I'm gussing that port 6881 is not open.  How can I open this port in ubuntu?

---

### Post by dbott67 on 2005-10-15
Are you behind a personal hardware firewall, such as a D-Link or Linksys DSL/Cable Router?

Or are you running one of the built-in software firewalls (i.e. firestarter, etc.)?

-Dave

---

### Post by racermike1967 on 2005-10-15
I'm gussing i'm behind a built-in firewall that came with ubuntu.  I never installed a firewall after installing ubuntu so whatever I have came with ubuntu.  Also I don't have a hardware firewall but I am on a school network.  I live in a dorm.

---

### Post by dbott67 on 2005-10-15
Are you trying to bit-torrent from the internet?  If so, it may be that the school's firewall is set to block port 6881 for legal reasons (you know --- downloading copyrighted materials, such as music, movies & software).

Normally, Ubuntu does not ship with a firewall enabled by default but that may have changed with the latest release of Breezy.  I'm going to check the forums to see if this is the case and I'll post my findings.

-Dave

---

### Post by Jussi Kukkonen on 2005-10-15
There is no firewall in the default install (no open ports either). I'm guessing your university is blocking the ports.

---

### Post by rah1420 on 2005-10-22
Here's a head-scratcher;  I have a Breezy build that I'm trying to run azureus on.  I get the 6881 NAT error same as the OP.  However, I'm on the same hub - literally - in my home office and on one of the other ports is a Win2k machine that is happily running Azureus over - yep, you guessed it - port 6881.

WTF, I think.

To my mind, it's obviously not an ISP issue.  I also opened up the port for my IP address on the linksys box.  My next step is to reset the router and bounce the ubuntu machine and see if everything starts to play nicely, but this is weird.

The only other thing I can think of is that this machine was installed with DHCP enabled, and I opened the port for a static non-managed IP address. (Class C non-routable netblock.)  So perhaps something deep in the bowels of this ol' badger still thinks I'm at 192.168.1.107 and not .75, which is where I really am now.

Any thoughts?

---

### Post by rah1420 on 2005-10-22
Okay, this is getting seriously weird.

I have an extra hard disk for the Win2k Thinkpad that is my "daily driver" machine.   (The win2k part is for school, not my idea.)  I threw it in, and installed Breezy on there, then Java and azureus.  I'll be dipped, but the damn thing works.

So what's different?   I have Java 1.4.2 on the misbehaving machine and 1.5 on the new one.    The one is a Dell mini-tower that's kinda old, and the other is a T23 thinkpad.

Now I'm hopelessly confused.  Should I try installing the new java?  I don't get it.

---

### Post by herrpoon on 2005-10-22
Were the win2k and ubuntu machines on the same network?  I've found that if I start a torrent in windows say on port 12345 and then try and run a torrent on ubuntu on the same port, I get no where...

Perhaps it's something to do with that.

---

### Post by rah1420 on 2005-10-22
Yeah, the same network -- but it doesn't matter if there's a client running on the other box or not.   Doesn't even matter if the machine's turned on or not.

Let's call them laptop and tower.   

Laptop can get to port 6881, and does the azareus thing no matter what OS is running, either win2k or ubuntu.  It has the Java 1.5 engine.  It lives at static IP 192.168.1.99 and the port is forwarded.

Tower can't get to 6881 to save its life.  I read here on the forum about a web based portscanner and I ran it; the port is open, so it's not that.   The machine's running breezy and has java 1.4 installed.   It lives at static 192.168.1.75 and that port's forwarded the same way.

To eliminate the router, I'm going to shut down the laptop and change the IP on the tower to .99, then try it.  If I can get through, it's the router.  If not, it's a machine problem.

Edit a few minutes later:  Yep, when I change it to .99 it worked.  now it's a router problem.  
I went into the router config and the only thing that was different was that both TCP and UDP were checked for the .75 address and only TCP was checked on the .99 address. 
Now it's all working.
Go figure.

Edit a few hours later:  Nope, it still reports that it has a NAT error; but it's sharing files, so I really don't care at this point.   I shot one other bug tonight on breezy so I'm feeling virtuous and victorious, and I'm gonna go have a beer and go to sleep.

The NAT Error problem persists...

---

