---
title: "Need help with wireless card"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by jonruiz1 on 2006-07-07
Hello,
I am new to Ubuntu, about 2 hours into it to be exact, and I am having trouble getting my wireless card set up. The device manager detects the card, but I can't add it in the network application because there is no Add button like the How-To's tell me. I am running on a dual boot Windows XP and Ubuntu, and I have the cards drivers on a .exe that I don't know how to open in Ubuntu. Could someone direct me to a program that lets me open .exe's or help me get my wireless card working?
Thanks,
Jon

---

### Post by uzi09 on 2006-07-07
try the NetworkManager program. it may or may not support your card. here's how to install it though:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by jonruiz1 on 2006-07-08
The NewtworkManager page isn't there anymore. Any other solutions to my problem? If it helps any, I'm using v5.10 not Dapper Drake.

---

### Post by coderboi on 2006-07-08
> **jonruiz1 said:**
> The NewtworkManager page isn't there anymore. Any other solutions to my problem? If it helps any, I'm using v5.10 not Dapper Drake.


hi

i had trouble installing it too.  I had to go to System > Administration > network (I think).  After getting there, I noticed my wireless card was known by the system but I had to manually enter the network name and things like that.  

have you tried this?

I'll bring up my linux box later and double check.

cb

---

### Post by rccharles on 2006-07-08
> **jonruiz1 said:**
> Hello,
 Could someone direct me to a program that lets me open .exe's or help me get my wireless card working?
Thanks,
Jon
Ubuntu allows you to use a native Linux driver or a Windows driver.

In order to use the Windows driver, you need to use the program ndiswrapper.  
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

For more information out wireless, see:
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Robert

---

