---
title: "do i need static ip?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by jordi_rc on 2007-02-24
Hi to all

I read many comments on spanish sites that say it is better a dynamic ip than a static ip.

I have static ip, as I want to run my server at home.

They say it is better a dynamic ip, and I am wasting money.

Is it true?

I don't want to use no-ip nor dyndns as I want to have my own full name and depend of the less number of external services as it is possible. I also don't want get into trouble with ips when I run my Java servlets and web server applications or configuring them. I don't want people going crazy to visit my server or access it too slow.
So I suppose I better use static ip.

Did I do a good choice choosing to have static ip?
Is it true that it is more secure to have a dynamic ip for A SERVER? Or it is a disavantage?

Thanks for replying

Jordi

---

### Post by irish_flu on 2007-02-24
My personal opinion-

Using a dynamic IP for a server does nothing to increase security, in my opinion.

I completely agree with you that a static IP would be better if you plan to run a server.  With a dynamic IP, there is no good way to know (without using dynDNS or one of those services you mention) if you will still have the same IP the next time you wish to access your server.

I use a static IP at my house (my router has the public static IP, then my machines have private static IPs behind that) too, I think you made a good choice.

---

### Post by jordi_rc on 2007-02-24
Thanks Irish-flu

You solved my doubts.
As you did a network similar to what I need, please can you give me some advice?

I have this:

- Xubuntu linux (great product) dapper drake

- A barebone computer

- A static ip address

- Xampp

- router thomson speedtouch 530v6, connected via ethernet to the Xubuntu machine, and with USB to Windows machine.

I want my Xubuntu machine to work as server. I want to be able to navigate with my xp machine even if I turn off my Xubuntu machine sometimes.

Is this possible?

--
How can I do this? I mean, that people from outside access my xampp server when they type my static ip. And not enter the xp machine.
In the menu that comes with my modem I see an option that says "assign a public ip to a device". It says it is for this, but I fear to break something, or maybe I need to do something more before.
--
Someone said me I must open the 80 port and route the private ip of my Xubuntu machine. Is that true?? Is that what that option does? ("assign a public ip to a device")
I am a bit confused.

How did you do it?

Thanks very much

Jordi

---

### Post by irish_flu on 2007-02-24
Hi Jordi,

I've never used USB and ethernet on a router at the same time, but I don't think you'll have any problems.  Both machines should use the router as their "gateway".

For having folks access stuff on your Xubuntu box through the router, you're going to want to use something called "Port Forwarding".

You'll want to refer to manuals for your specific router to figure out how to set that up.

As an example, let's say you wanted to set up a webserver, which would normally use port 80.  You tell the router "when traffic hits <public IP> on port 80, send the traffic to <private IP of Xubuntu machine>".

---

### Post by jordi_rc on 2007-02-25
Thanks irish_flu

So I suppose that I must do this:

- identify traffic acceding externally on port 80 to Xubuntu machine. 

But what must I do??:

- identify my Xubuntu pc with my static ip?? Or use my private ip (	192.168.0.129 ??) with the external traffic ???

My modem manual is a bullXXXt, so do you know some resource to configure it on Xubuntu? I mean, to open the ports and forwade traffic to them? Firestarter? Or another one? Some website?

Is there a general way to do that? Or changes between router models?

--

Another question:

People in a spanish forum about help to adsl issues said me that about ip static being insecure. I think it is a nonsense. They insist one is more vulnerable with static ip than with dynamic ip to these attacks: ip spoofing, ddos, dumping, sql injection, and making a mail server in your machine to spam. I think all those attacks are prevented by coding techniques and not depend on ip. Am I right?

Thanks

Jordi

---

### Post by jordi_rc on 2007-02-25
In addition to my last post:

I found a website that says how to forward ports in my router

[http://www.portforward.com/](http://www.portforward.com/)

Though it only explains how to configure static ip on Xp and even for Xp it is a bit outdated.

Do you know how to do it in Xubuntu?

Jordi

---

