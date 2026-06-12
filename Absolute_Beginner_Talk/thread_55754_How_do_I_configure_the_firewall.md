---
title: "How do I configure the firewall?"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by accessa on 2005-08-10
I just installed Kubuntu, when I run a Port scan test all ports are visible but closed.
I  want to hide them, how do I increase the safety in Kubuntu ?
I have KDE and cant find the firewall.

Im a noobie so please explain simple and step-by-step.
 :roll:

---

### Post by dave9191 on 2005-08-10
Are you running any services like a web server or a mail server on your computer or any other services? Is your compuer being used as a gateway for a network? If the answer is no to both of the questions you dont need a firewall. This is linux, not windows. 

But if you are still determined, then at [www.ubuntuguide.org](www.ubuntuguide.org) you can find instructions on installing firestarter :)

Dave

---

### Post by nic2 on 2005-08-10
Will a service like 'Samba server' leave one vulnerable?  I also mount my Windows partition on boot, does this present any security risks?

---

### Post by KingBahamut on 2005-08-10
apt-get install firestarter 

or

Search for firestarter in Synaptic and install it. 

You can set it to auto start, and add all the nessecary rules from there. 

Just remember that its rather restrictive by default, so youll need to configure it and so forth.

---

### Post by pmjdebruijn on 2005-08-10
Jup, firestarter rocks...

Regards,
Pascal de Bruijn

---

### Post by Ubunted on 2005-08-10
All I do is install it and run the configuration wizard in the app menu and leave it at that. According to their website that's all you need to do, and I've never had a problem doing it that way.

---

### Post by dave9191 on 2005-08-10
[QUOTE=nic2]Will a service like 'Samba server' leave one vulnerable?  I also mount my Windows partition on boot, does this present any security risks?[/QUOTE]

Mounting windows partions is not a security risk. But the samba server... well slap a firewall on just in case :) 

Dave

---

### Post by az on 2005-08-10
If you are running kde, guarddog runs pretty well...

---

### Post by pmjdebruijn on 2005-08-15
[QUOTE=dave9191]Mounting windows partions is not a security risk. But the samba server... well slap a firewall on just in case :) 

Dave[/QUOTE]

Uhm well firewall don't magically make your server invulnerable... When running samba with it's ports open in the firewall, it won't make your server any more secure...

Regards,
Pascal de Bruijn

---

### Post by dave9191 on 2005-08-16
[QUOTE=pmjdebruijn]Uhm well firewall don't magically make your server invulnerable... When running samba with it's ports open in the firewall, it won't make your server any more secure...

Regards,
Pascal de Bruijn[/QUOTE]

But you can stop access from the internet and only allow LAN access to the samba if you set your firewall up to do packet filtering :)


Dave

---

### Post by sophtpaw on 2005-08-16
You can set it to auto start, and add all the nessecary rules from there. 



how come then, although i have 'start/restart firewall on program startup' ticked in Firewalls preferences, i always need to launch it manually from Applications/System Tools? i really would prefer not having to do so, and give the password everytime too, when i start-up

--
sophtpaw

---

### Post by Freddd on 2005-11-24
I'm having the same problem as the person in the post above me. Is there no way to  get the firestarter to autostart?

---

### Post by jorn on 2005-11-24
>System>Preferance>Sessions>Started Programs. Apply "gksudo firestarter"
But you have to tap the password on startup. That's what I can help with .
Jorn

---

### Post by user1397 on 2006-06-20
so that you don't have to type in the password, type ```
sudo firestarter -start--hidden
``` instead of ```
gksudo firestarter
```

---

