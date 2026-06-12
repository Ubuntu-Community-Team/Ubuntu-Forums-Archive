---
title: "No connection under Ubuntu."
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by PirateBob on 2006-08-29
I am a general noob when it comes to Linux. However, I've been around computers my whole life, and am more than capable of figuring out most problems without resorting to questioning the masses. I attempted to search for an answer to my question, but I do not have enough of the specifics to get results anywhere within the triple digits.

My problem is simple, I have NO connection to the internet when I'm using Ubuntu. I'm using a static IP, the same as my setup for windows. I have all the "Enable Connection" boxes checked. I simply have no connection.

I'm using a wired router, if that helps in any way.

ANY help would be appreciated. Thank you.

---

### Post by Josh_b on 2006-08-29
So can you ever get online? Like after you've restarted from your windows partition? Try deactiviating/activating your ethernet device (**System->Administration->Networking**).

Hope that helps,
Josh

---

### Post by PirateBob on 2006-08-29
the same settings work perfectly on my Windows boot. I'll try that, wish me luck!


Thanks :)

---

### Post by Josh_b on 2006-08-29
Yeah, I have the same settings for Windows and Linux and if I boot straight into Linux, I have to reactivate my connection, but if I boot into windows, restart the machine and boot into linux, it works straight away. I'm not sure how to permanently fix it though.

Josh

---

### Post by PirateBob on 2006-08-29
No such luck.  It's 5 in the morning. I give up for the night... sorry, Morning. If anyone can post something that might help while I'm sleeping, it would be very much appreciated.
I'll probably think of exactly how to fix it just before I fall asleep, and forget it in the morning. So I'll check this when I wake up (5 hours, tops).  Thx Mates!

---

### Post by steve.horsley on 2006-08-29
I wish I could get by on so little sleep.

Can you post the output of these commands?
> ifconfig
route -n
cat /etc/network/interfaces
cat /etc/resolv.conf

If you have gone for a static IP address, I suspect you may be missing the configuration for a default route and for your DNS servers. The above should tell us it that's it.

---

### Post by PirateBob on 2006-08-29
I did those commands, the output was a bit lengthy, so i attached it.

(Just start going to sleep at 12, then waking up half an hour earlier every other week)

---

### Post by PirateBob on 2006-08-29
Additional Info:
I have checked in the compatability table for my Ethernet card. I have an SiS900 (Integrated piece of crap) and it IS compatable, and it's also auto-detected, so that isn't the problem.

One little thing that might help. I have NEVER been given a hostname or password, I'm not sure if I need to obtain one or what, but that might be my problem. I'm going to call my ISP and ask what it is, and I'll try that out. I'll post anything else I figure out.

Edit: I'm also going to try to connect without using the router. Just to see if that stupid thing is my problem.

---

### Post by Druidor on 2006-08-29
I Posted this in the forum a short while ago in the efforts of helping someone else but it seems apt for your problems too.


on Dapper

**System>Administration>Networking**


**Ethernet connection>Properties**

Tick Enable this connection

**Configuration: Static IP address**
IP address: 10.0.0.5
Subnet mask: 255.255.255.0
Gateway address: 10.0.0.2 (My router is ip 10.0.0.2)

**Under DNS**

**DNS Servers**
195.8.69.7
195.8.69.12

This DNS information is from my ISP

I have found if you have not put the DNS information in then the internet connection does not work.

---

### Post by PirateBob on 2006-08-29
Hmmm... I need to contact my ISP in order to get the info. (They are wildly stupid, I'm just going to SAY the word Linux and they'll call me a hacker) Altentativley, couldn't I just use a command prompt in windows, then "ipconfig /all" to obtain the same information?

---

### Post by sbassett on 2006-08-29
> **PirateBob said:**
> Hmmm... I need to contact my ISP in order to get the info. (They are wildly stupid, I'm just going to SAY the word Linux and they'll call me a hacker) Altentativley, couldn't I just use a command prompt in windows, then "ipconfig /all" to obtain the same information?

Yes you could, I would suggest this. I don't know if this was mentioned or not, but grab your Default Gateway while you are there.

---

### Post by PirateBob on 2006-08-29
Yes, as I've said, I have the exact same settings as I do under windows, including a complete static ip setup. (Default gateway, etc.) I've just uplugged the router, and am going to boot into Ubuntu again. See you on the other side!

---

### Post by PirateBob on 2006-08-29
Well, it worked *better* with the router unplugged. It seemed to send out packets, but not recieve any.

I am genuinley stupmed.

---

### Post by aran384 on 2006-08-29
you seem to be having a similar problem to me... :s

---

### Post by steve.horsley on 2006-08-29
PirateBob: Your DNS server seems to be set as 192.168.1.1 but your router set to 192.168.0.1. Maybe this is the problem. 

ipconfig from your windows would be very enlightening. Don't know why I didn't think of that.

---

### Post by PirateBob on 2006-08-29
My ipconfig as follows

C:\Documents and Settings\thing_bob>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : THINGBOB
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : SiS 900 PCI Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-0D-87-83-F7-6B
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.0.4
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1

C:\Documents and Settings\thing_bob>



(The IP address listed is from the 4th port on my router, when you had me do those commands, I was using the first)

---

### Post by PirateBob on 2006-08-29
Alrighty, I give up. 

I'm going to stop checking this thread. I'm sure people will get annoyed if it keeps getting bumped.

Drop me a PM if you can help, or add me to msn: [email]pirate.bob@hotmail.com[/email]

Thank you VERY much to all the people who have helped me already.

---

### Post by Druidor on 2006-08-30
Well It may help to know your ISP so we can look into what DNS numbers they use. But from what you have given so far I would suggest the following settings in your network configuration on Ubuntu

**System>Administration>Networking**

**Eth0 Ethernet connection>Properties**

Tick Enable this connection

**Configuration: Static IP address**
**IP address:** 192.168.0.# (# new IP number within range set in your router)
**Subnet mask:** 255.255.255.0
**Gateway address:** 192.168.0.1 (Your Router IP)

[B]Under DNS

DNS Servers[/B]
This is the bit of info required from your ISP it is normally available on their web sites. but I think it is the bit that is stopping you getting a connection.

**e.g. my ISP Claranet**

[http://www.uk.clara.net/support/misc_serversettings.php](http://www.uk.clara.net/support/misc_serversettings.php)

& If I type the DNS number in at this site it will tell me that it belongs to claranet my ISP

[http://www.internetfrog.com/index.asp?source=google](http://www.internetfrog.com/index.asp?source=google)

The DNS numbers you are using do not display here so I believe there is someting wrong with those numbers.

---

