---
title: "Where can I find my IP?"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by sixpointeight on 2007-01-20
Where can I find my Computer's I.P. Address? All I can find are my router's and IPv4 address.

I am running Ubuntu Edgy 6.10 with an apache webserver.


Also, how do I get a direct Lan hook-up to the internet to work? Because when I try plugging the internet box into my computer it doesn't work.

---

### Post by norman_ on 2007-01-20
[www.whatismyip.com](www.whatismyip.com)

Edit: I don't understand your second question.

---

### Post by zerhacke on 2007-01-20
> **sixpointeight said:**
> Where can I find my Computer's I.P. Address? All I can find are my router's and IPv4 address.

I am running Ubuntu Edgy 6.10 with an apache webserver.

You can find your private IP by opening a terminal and typing the command "ifconfig" without the quotes, then pressing enter.


> Also, how do I get a direct Lan hook-up to the internet to work? Because when I try plugging the internet box into my computer it doesn't work.

I'll bet it works.  If it didn't work plugging your server directly to the modem wouldn't solve anything.  What I bet is happening is IPv6 is causing some serious slowdown.  I don't know why they even turn IPv6 on, it's not like it's a standard yet or even close.

Look into my posting history to find out how to disable IPv6.

---

### Post by norman_ on 2007-01-20
> **zerhacke said:**
> You can find your private IP by opening a terminal and typing the command "ifconfig" without the quotes, then pressing enter.

Not if you're behind a router

---

### Post by aktiwers on 2007-01-20
```
ifconfig
```:)

EDIT:
You beat me norman :)

---

### Post by Zimmer on 2007-01-20
> **sixpointeight said:**
> 
Also, how do I get a direct Lan hook-up to the internet to work? Because when I try plugging the internet box into my computer it doesn't work.

If by 'Internet Box' you mean a router or a Gateway computer linked to the Internet then may I suggest you have that running and connected to your Ubuntu machine before you boot Ubuntu.... The Ubuntu start sequence should then detect the hardware and the  network settings etc.

---

### Post by billingsworld on 2007-01-21
Not sure what you had prior to the problem, but, where I live, the DSL provider locks in your first MAC address of the device you connected.  If you had a router that was sharing your internet connection and you unplug it and go from your DSL modem to your PC you know have a different MAC and you need to tell your ISP that you have a new MAC address.  Router's have a clone MAC option that makes it easy to do the reverse of what you have done.

Also, I have experience with our local cable internet provider and their Motorola cable modems store a maximum of two MAC address, if you plug in a third device, you need to contact them to reset the Cable modem.

Not sure if this helps you, you could have just a bad cable!

---

