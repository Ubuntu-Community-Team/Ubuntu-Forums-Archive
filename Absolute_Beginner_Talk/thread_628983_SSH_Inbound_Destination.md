---
title: "SSH Inbound Destination"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-12-01
Thanks to Dr.Small's guide here I have set up my machine for SSH and am now at the end of the guide where things are getting slightly confusing as to how to proceed > [http://php.8ez.com/drsmall/blog/?p=124]("http://php.8ez.com/drsmall/blog/?p=124")

I'm in my router right now (D-Link DI-524) and am confident on opening port 22 but I'm just confused on my IP address since it's a router and it's DHCP and I assume my ISP is doing the same, how can I assign a static IP to my machine that will be accessible anywhere so I can SSH into my machine if I travel to Brasil or something.

---

### Post by Dr Small on 2007-12-01
If your ISP is giving you a Dynamic IP, there is no way to make it staic, but if your network (router, internal) IP is dynamic, and constantly changes, then you can change that under Network to be a static IP Address.

---

### Post by siciliancasanova on 2007-12-01
So I'm out of luck since my ISP is giving my router a dynamic IP?

---

### Post by Dr Small on 2007-12-01
Well, your ISP does't give your router an IP, it gives your modem an IP.
There is a difference.

The router is your own personal network device. You configure it, and setup DHCP or Static IP addresses. Now on the otherhand, the modem which is how you receive an internet connection is controled by your ISP. If they have set your modem up for DHCP (Dynamic IPs) and you external IP address continually changes, then yes, you are somewhat out of luck.

But your ISP using DHCP in no way effects your router.

But, my IP is dynamic, yet it doesn't change unless the modem is turned off for 24 hours. Other's are different, so you may have to check that out too.

---

### Post by siciliancasanova on 2007-12-01
Got it, thank you for the help.

---

### Post by mellowd on 2007-12-01
You can use something like dyndns.

My IP changes but I'm always able to get in because dyndns automatically updates my dns entry with my new ip address

---

### Post by Dr Small on 2007-12-01
> **mellowd said:**
> You can use something like dyndns.

My IP changes but I'm always able to get in because dyndns automatically updates my dns entry with my new ip address
How the heck does it do that ???

---

### Post by mellowd on 2007-12-01
> **Dr Small said:**
> How the heck does it do that ???

Well I've set my firewall to do the hard work. Every 4 hours it connects to dyndns.org and gives it my current IP address. It only changes ever couple of days but it's all automatic now.

Have a look here: [http://www.dyndns.com/](http://www.dyndns.com/)

---

### Post by monte48lowes on 2007-12-01
I have ddclient installed on my desktop. I installed it from the repositories and ran the setup. There are some other options available here:

[https://help.ubuntu.com/community/DynamicDNS]("https://help.ubuntu.com/community/DynamicDNS")

There is not much information there regarding ddclient. So here is a quick how-to:

1. Register with dyndns.org. Record your hostname and password
2. Install ddclient and input the information for your dyndns account

You will still have to configure your router to forward the necessary ports you want to access to your computer.

Mike

---

### Post by Dr Small on 2007-12-01
> **mellowd said:**
> Well I've set my firewall to do the hard work. Every 4 hours it connects to dyndns.org and gives it my current IP address. It only changes ever couple of days but it's all automatic now.

Have a look here: [http://www.dyndns.com/](http://www.dyndns.com/)
That would be a cool tutorial to write up.

---

### Post by mellowd on 2007-12-01
> **Dr Small said:**
> That would be a cool tutorial to write up.

I wouldn't mind writing a tutorial up, but I'm using an external netscrren firewall, which I think would be pretty rare here.

---

### Post by Dr Small on 2007-12-01
> **mellowd said:**
> I wouldn't mind writing a tutorial up, but I'm using an external netscrren firewall, which I think would be pretty rare here.
Oh, well that is different then. Do you think it could be done with iptables somehow ?

---

### Post by mellowd on 2007-12-01
As far as I am aware, you can already do it straight with your linux box.

---

