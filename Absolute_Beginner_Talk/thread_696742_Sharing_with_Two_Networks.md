---
title: "Sharing with Two Networks"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Aysah on 2008-02-14
I recently asked the boards questions about setting about setting up a web server 
[http://ubuntuforums.org/showthread.php?t=693948]("http://ubuntuforums.org/showthread.php?t=693948")
and I have some slightly more "advanced" (to me at least lol) questions to add on.

My setup is as follows, thanks to the help of LeChacal...

--> ISP MODEM ---> Ipcop (split)
network #1 DHCP capability ---> Switch/Router --->PersonalComputers
network #2 static IP ----> WebServer

Both the Web Server and my Home Network have diffeent Address Pools for security purposes.  My question is how would I go about adding a FileSever that both the WebServer and HomeNetwork can access?

**Only Options I've seen so far..**
[LIST=1]
[*]Would be as simple as just setting rules on IPCOP?
[*]An IT at work mentioned the following but it didnt seem correct. He said the router can be used to connect the two switches and then with proper config of the router I can achieve what I need to do.
--> ISP MODEM ---> Ipcop (split)  --> "Intelligent" Router
network #1 DHCP capability ---> Switch --->PersonalComputers
network #2 DHCP capability ---> Switch --->WebServer & File Server
It seems redundant thought because why do I need a router to do this if I already have Ipcop?
[/LIST]

---

### Post by dstew on 2008-02-14
I think a lot depends on what Ipcop can do. Can it act as a bridge between two subnets? If so, you would have no problem. But if not, I think the intelligent router is the way to go.

---

### Post by KCPokes on 2008-02-14
You need to set up IPCop to allow pinholes between your green network, which is your Home Network, and your orange network, which is essentially your DMZ in which your webserver resides.  This really is more of a question to pose to IPCop forums as it really is based on the capabilities of IPCop.

---

### Post by Aysah on 2008-02-14
> **dstew said:**
> I think a lot depends on what Ipcop can do. Can it act as a bridge between two subnets? If so, you would have no problem. But if not, I think the intelligent router is the way to go.

any suggestions on a reliable router that can support this?

---

### Post by Aysah on 2008-02-14
> **KCPokes said:**
> You need to set up IPCop to allow pinholes between your green network, which is your Home Network, and your orange network, which is essentially your DMZ in which your webserver resides.  This really is more of a question to pose to IPCop forums as it really is based on the capabilities of IPCop.

you bring a valid point to the table... I should pay their forums a visit.  I just figured maybe someone knew of any other software or linux solution around this mess... Thanks

---

