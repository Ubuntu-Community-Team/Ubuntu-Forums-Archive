---
title: "Firefox oddity"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-04-07
Hi Group,

So, as I browse the web, from time to time Firefox pops up a Can't Connect window.

I press retry and sometimes it connects.........sometimes three clciks sorts it out.

I'd think that it was a router firewall problem except for the fact that most of the time, it works

Questions:-

1) How do I find the ISP address of THIS computer?
2) If I find it, I suppose I'd be able to set permissions within my router firewall?

Thanks,
Phil

---

### Post by Xoanan on 2007-04-07
> **groeswenphil said:**
> Hi Group,

So, as I browse the web, from time to time Firefox pops up a Can't Connect window.

I press retry and sometimes it connects.........sometimes three clciks sorts it out.

I'd think that it was a router firewall problem except for the fact that most of the time, it works

Questions:-

1) How do I find the ISP address of THIS computer?
2) If I find it, I suppose I'd be able to set permissions within my router firewall?

Thanks,
Phil

The quickest way to find out your ip address is to open the Termial --> type in **ifconfig**.  This will give you the ip address that is being assigned to your pc;  

As for the router, you usually need to check that through router&#347; main menu.  The method I use is to open my browser and type in the router ip(your can get that from the router&#347; documentation).  This will get you into the router menu

I didn do much with it, as I am set up strictly DHCP through Comcast.  I also never use MTU size as it is not required by my ISP.

Hope that helps8-)

---

### Post by groeswenphil on 2007-04-08
Typed this

philip@concertina:~$ ipconfig

and got this


bash: ipconfig: command not found

Is it broken?
Phil

---

### Post by eentonig on 2007-04-08
under linux it's called

> ifconfig

or, if you have more then one network card


> ifconfig eth0

> ifconfig eth1

> ifconfig wlan0

---

### Post by groeswenphil on 2007-04-08
[COLOR="Red"][SIZE="7"]That Worked !:guitar: Thanks. Phil[/SIZE][/COLOR]

---

