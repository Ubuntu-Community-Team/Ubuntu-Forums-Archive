---
title: "Two fundamental problems"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by unityofsaints on 2007-09-22
Hey,

(Not sure if this belongs here so feel free to move mods)

I can't get 1) torrents or 2) filesharing with windows working.

Problem 1:
- ubuntu machine set to static IP
- portforwarding set up using that static IP
- bittornado set to use the ports forwarded (10000-10010)

Still only a yellow light instead of a green one and mediocre speeds :(

Problem 2:
- filesharing worked sparodically on my previous 7.04 install, now on 7.10 with all updates
- have set the correct workgroup name and enabled shared folders
- windows machine also set to correct workgroup name, folders shared
- network and switch are fully functional
- tried searching for the ubuntu machine by name using search for computer function on the windows box, doesn't work

Still folders don't show up and/or can't connect to them :(

Any help greatly appreciated!

---

### Post by agurk on 2007-09-22
Problem 1: install Firestarter and open the ports you need.
Problem 2: In Windows, click Start --> Run... and type \\192.168.1.20 (or whatever your Ubuntu box' IP is). Does that work?

---

### Post by Sef on 2007-09-22
> Problem 1: install Firestarter and open the ports you need.

Applications > Add/Remove > Search > type in Firestarter > click on the box > click apply twice > Finish

---

### Post by zilebune on 2007-09-22
> **unityofsaints said:**
> 
Problem 2:
- filesharing worked sparodically on my previous 7.04 install, now on 7.10 with all updates
- have set the correct workgroup name and enabled shared folders
- windows machine also set to correct workgroup name, folders shared
- network and switch are fully functional
- tried searching for the ubuntu machine by name using search for computer function on the windows box, doesn't work

Still folders don't show up and/or can't connect to them :(

Any help greatly appreciated!

Sounds to me like a Samba problem. Maybe the upgrade to Gutsy left out some custom config file...try starting Samba by hand (supposing the configs are still there and healthy):

```

sudo /etc/init.d/samba start

```

and also check the logs in /var/log/
If the issue still bugs you maybe you should search the forum for Gutsy - Samba related problems.

---

### Post by unityofsaints on 2007-09-22
> **agurk said:**
> Problem 1: install Firestarter and open the ports you need.
Problem 2: In Windows, click Start --> Run... and type \\192.168.1.20 (or whatever your Ubuntu box' IP is). Does that work?

Neither of them worked :(

Thanks for the help anyway.

---

### Post by agurk on 2007-09-23
Hmm, this port range puzzles me:> - bittornado set to use the ports forwarded (10000-10010)
You only need to open one TCP server port, what's with the range?

---

### Post by unityofsaints on 2007-09-23
> **agurk said:**
> Hmm, this port range puzzles me:
You only need to open one TCP server port, what's with the range?

Portforward.com recommends this port range for bittornado, but I've tried opening a single port too without any success :(

---

### Post by agurk on 2007-09-23
Ok, I see. Well, my bet is that the problem is to be found in the port forwarding stuff, the devil is in the details. In order to narrow down the search a bit, you could try scanning your Ubuntu box for open ports by running [nmap](http://insecure.org/nmap/) on your Windows box. If it shows that the Bittornado port is open, the problem is likely in your router configuration. Keep Bittornado running while scanning with nmap.

---

### Post by mandrill on 2007-09-28
Don't know if you've got an answer or not on Problem #2, but it sounds like a Master Browser problem - especially if part of your network is wireless, or you are sharing with Windows, or both.

---

