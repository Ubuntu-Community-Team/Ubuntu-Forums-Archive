---
title: "New Confused user"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by s_raghu20 on 2006-05-15
Hi,

Though I have had a "touch" of Linux experience with Mandrake 9 but that was about 2-3 years back. Even though I had the enthusiasm, it never materialized that I became a dedicated linux user.

Now I just managed to borrow a friend's laptop for a few weeks and he had installed Ubuntu on that. I am having serious trouble getting my cable modem to talk to the system. 

Here's what I have done (still unsuccessful in getting it work). Apparantly, the packets are coming in, but going out is a problem.

1. System -> Administration -> Networking -> Ethernet connection (is active) -> properties
    Here I have to choose configuration as DHCP, since my internet service provider has not given me any static IP address.
    When I do that (choose DHCP), the three text boxes for ip address, subnet mask and gateway address are disabled. 

2. Well, then I try to specify the DNS servers I am supllied with by ISP. 

I have also tried to specify the "Default Gateway device" to eth0 (my ethernet card's logical name - i suppose), but its reset every time i open the dialog again.

A. Where do I enter the gateway address ?

When I try to do a ping to any address (already tried with gateway ip, dns ip), nothing works.

3. System -> Administration -> Network Tools
    Here I tried ping, no response. Though the devices tab shows that its continuously receiving packets, neither ping nor traceroute can find something.

My version is installed on an Ibm T22 laptop. The friend I borrowed this laptop from was able to use internet properly. Unfortunately he can't helpt me since he is away. My OS is Ubuntu Dapper Beta.

Desperately looking for help..

best regards
raghav..

---

### Post by whitey on 2006-05-15
Hello,

If you have Road Runner style cable internet, you'll want to unplug your modem for 15 secs, to reset it (everytime you switch the computer connected to it, until you get a router).  Then restart your laptop to recieve a proper DHCP automatic connection, which more than likely your modem supports.

Good Luck

---

### Post by s_raghu20 on 2006-05-15
can someone help me... please....
this place is my last resot for help...

pls....

---

### Post by s_raghu20 on 2006-05-15
can someone help me... please....
this place is my last resot for help...

pls....

---

### Post by snaga on 2006-05-15
If you have chosen DHCP, then you shouldn't have to put in the gateway or DNS server info. the DHCP server should provide that to your machine.

Are you rebooting or otherwise causing networking to restart? Rebooting the machine would also do this, obviously.

I would suggest opening a command line console and typing this, after setting the network to DHCP:

sudo /etc/init.d/networking restart

after that, type 


ifconfig eth0 | grep "inet addr"


That should show an IP address. If it doesn't, you're still not connected.

---

### Post by s_raghu20 on 2006-05-15
Hey snaga,

Can't thank you enough. the restarting of the networking service was the real problem it seems.

Thanks a ton. I love it.

:) Thanks a ton.

Writing this message from the linux box already. Thanks once again.

---

### Post by snaga on 2006-05-15
Glad to help. Welcome to Ubuntu.

---

