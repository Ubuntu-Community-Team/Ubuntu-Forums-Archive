---
title: "nmap?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2007-12-21
i'm trying to download it and it's not there? like when i try to download it for the nmap site it says file not found. do you know where i can get it or a program like it?

---

### Post by RadiationHazard on 2007-12-21
well actually. i already have it installed. how do i get it running? it's not showing up in my menu or i don't see it atleast.

---

### Post by dannyboy79 on 2007-12-21
nmap is a terminal based app and it won't add a selection within your applications location unless you custom add it. You can use the menu editor within System, Preferences, Menu. You can simply open a terminal, then type in 

nmap [Scan Type...] [Options] {target specification}

you'll have to read the man page for nmap as their are many many options and ways to run nmap. Just you're aware, it won't work if you try to nmap yourself. If you want to see which ports are open on your own box, enter this command

netstat -pant

and all ports that start with 0.0.0.0:XX are open the world (the XX represents the port number) BUT only if you have forwarded that port within your router (if you have a router) If you don't have a router, I would strongly suggest using firestarter (it's a firewall) or buy a router. It'll protect you from very BAD people.

---

### Post by RadiationHazard on 2007-12-21
thank you!

---

### Post by RadiationHazard on 2007-12-21
ok guys i'm sorry i just don't understand how this works? can someone please explain and them give me a link to what i should read and stuff?

thanks

---

### Post by bodhi.zazen on 2007-12-21
/bodhi hands RadiationHazard Google

[http://lifehacker.com/software/security/how-to-portscan-your-computer-for-security-holes-198946.php](http://lifehacker.com/software/security/how-to-portscan-your-computer-for-security-holes-198946.php)

[http://www.nmap-tutorial.com/html/nmap-tutorial-single.html](http://www.nmap-tutorial.com/html/nmap-tutorial-single.html)

---

### Post by The Cog on 2007-12-21
You may prefer a GUI front end to nmap - try installing package **nmapfe**.

---

### Post by bill_greene on 2008-01-02
> **The Cog said:**
> You may prefer a GUI front end to nmap - try installing package **nmapfe**.

Thanks I was looking for something like that. :)

---

