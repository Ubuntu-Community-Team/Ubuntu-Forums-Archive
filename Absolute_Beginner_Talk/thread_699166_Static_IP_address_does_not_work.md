---
title: "Static IP address does not work"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by snakelock on 2008-02-17
Hi there,

It is the first time I have installed Ubuntu iin my live and I am extremely impressed-the speed, the number of applications already there, updates only once.  Last week I have installed Windows XP from fresh on another computer :(:(:(

However, I still have to get used to the different ways of doing things  but this should be just a questions of time.

My Problem:
I want to give my computer a fixed IP address rather than let it run in roaming mode
In network etc I ticked static IP adress
gave my computer one 192.168.2.8 
submask 255.255.255.0
Default gateway 192.168.2.1 (my Router)
but I can not connect to the outside word.  If I tick the roaming mode everything is fine.
Is there something else I have missed?
Thank you
Snakelock

---

### Post by jrusso2 on 2008-02-17
You need to put your DNS information from your ISP

---

### Post by steefjeqv on 2008-02-17
Hi,

Can you send a ping to your router when using the static IP ?

Type in terminal :

sudo ping 192.168.2.8

If this doesn't work you may have to configure your router to use this specific IP.
I had to do so for my Linksys AG041.

Greetings,
Steven

---

### Post by snakelock on 2008-02-17
> **jrusso2 said:**
> You need to put your DNS information from your ISP

My router connects to the internet, not my computer.

---

### Post by jan quark on 2008-02-17
you have to..

well I had to define a static ip address in my router configuration menu first

---

### Post by talsemgeest on 2008-02-17
So there is no cable or connection between your router and your computer?

---

### Post by snakelock on 2008-02-17
> **talsemgeest said:**
> So there is no cable or connection between your router and your computer?

It is a wired connection.

---

### Post by seventhc on 2008-02-17
can you ping 192.168.2.1?
Also, not that it's necessary but have you tried rebooting?
I would also make sure no other computer has the 2.8 or it will conflict, I know this probably isn't the case, just pointing it out as it is a possibility.

---

### Post by ace007 on 2008-02-17
The previous post was correct, you must enter the DNS information when entering the static IP/router IP in network settings

---

### Post by snakelock on 2008-02-17
I am non wiser :(.

When eth0 set as roaming I have access to my router-ping works fine
As soon as I change the setting to static IP I loose the connection- ping gives no response 
I have a Netgear router WPN824

I have tried to reserve the static IP address on my router-no luck.  I specified a static route-still no luck.

Out of interest I changed my laptop from automatic to static IP address and it works.

---

### Post by seventhc on 2008-02-17
>  Out of interest I changed my laptop from automatic to static IP address and it works.Actually, thats where I thought you were changing it.

---

