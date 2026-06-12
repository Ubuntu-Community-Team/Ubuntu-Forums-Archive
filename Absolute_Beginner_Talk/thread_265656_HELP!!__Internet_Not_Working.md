---
title: "HELP!!  Internet Not Working"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by danthebugman on 2006-09-26
I installed Ubuntu on my laptop (Gateway MX7118, AMD Athlon 64) and now I cannot get the internet connection to work.  Neither the wireless or when I plug in the ethernet cord from my DSL modem :???: .  I've been going through the forums trying to get it up and running but I must admit that I'm rather lost at this point.  Can someone help me out here?
Before installing Ubuntu (completely, no more Windows XP :-D ) I was using the Live CD to gain a feel for it and I really really like it, but I need to have internet capabilities.
Thank you in advance for any help anyone can give.

---

### Post by Kobalt on 2006-09-26
Hi,

Is your modem a simple DSL ethernet modem or is it a router as well ? 
If it's a router, it should connect your computer directly at boot (otherwise there's a problem with your ethernet card, being not recognised or something like that...).
If it's a simple DSL ethernet modem, then you need to configure your connection with this command : 
```
sudo pppoeconf
```
Answer the questions and you're done. 

Cheerio !

---

### Post by deadgobby on 2006-09-26
Wireles card can be a tad tricky. So what type of wireless card are you using.
Gobby

---

### Post by danthebugman on 2006-09-26
Yes, my modem is just a simple DSL modem and I tried the sudo pppoeconf command in the terminal what I got was:

> Sorry scanned 2 interfaces, but Access Concentrator of your provider did not respond.

So where to now??
And my wireless is Broadcom 082.11g Network Adapter.

Thanks again for the help!

---

### Post by Kobalt on 2006-09-26
For your wifi card, have you checked [this HowTo]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom") on Broadcom cards ? 

About your pppoeconf answer : you can try first to kill an existing pppoe process running : 
```
ps aux|grep pppoe
```
note the first number in the line : the process id
```
sudo kill -9 <process id>
```
You can also try pppoeconf with a precise interface, according to your eth interface, for example : 
```
sudo pppoeconf eth0
```

Cheerio !

---

### Post by danthebugman on 2006-09-26
No, I had not found that How-To...thanks a bunch I'll see if it works.

Thanks for the other help also, I'm going to go try it out.

---

### Post by njparton on 2006-09-26
I cured this with my installation by delving into network settings and noting down the IP address of one of the DNS servers that should be in there if you're using DHCP.

Ping that IP address using a terminal window and see if liven things up.

---

### Post by danthebugman on 2006-09-26
Still a no go ](*,)  :-k 

Trying to kill an existing pppoe process results in the following:
> syntax error near unexpected token 'process id'

And I tried the sudo pppoeconf eth0 command and after answering some questions still no internet.

Third time's a charm? :rolleyes:

---

### Post by njparton on 2006-09-27
Have you tried pinging one of your DNS servers to try and wake things up?

---

### Post by gumbald on 2006-09-27
> **danthebugman said:**
> Still a no go ](*,)  :-k 

Trying to kill an existing pppoe process results in the following:


And I tried the sudo pppoeconf eth0 command and after answering some questions still no internet.

Third time's a charm? :rolleyes:

You did enter the process ID rather than "process ID"?

---

### Post by danthebugman on 2006-10-03
;) yes I put in the real process ID as opposed to "process ID".

I found the following while doing a search on the net has anyone tried it will it help?

Oh and thanks for the link to the how to on my wireless but of course I'm just lucky enough to have the one wireless card the results have been not so hot with 8)

---

### Post by danthebugman on 2006-10-03
LOL completely forgot to put the link...
[http://www.linuxant.com/driverloader/"]("http://www.linuxant.com/driverloader/")

There ya go.

---

