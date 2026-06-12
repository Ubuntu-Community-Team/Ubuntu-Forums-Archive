---
title: "amule"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-02-26
Hello, I'm using amule, and it will tell me that i've got a low id. The connection goes through a wireless LAN router and a Dsl to an isp. How do I know, where the necessary port is being blocked, and is it possible, that it comes from a firewall inside ubuntu. By the way, how do i know, which version of ubuntu i've got?

---

### Post by Sandlst on 2006-02-26
If you have firestarter installed you can right click on the firestarter icon in the system tray located somewhere around the top-right hand corner of the screen, run amule, and it should detect the in/out bound hit-I cant remember exactly where to see this, but by clicking the policy's tab (I think) you can create a new policy that will allow programs to use the ports you specify without being blocked....I dont have firestarter installed right now so I unfortunatly cant check for you, but its somewhere along those lines-to check which version of ubuntu you have installed, click System/Help and under the link "About Ubuntu" it should say something along the lines of "A short description of Ubuntu (insert ver. number here).  I cant help with the router if that is indeed blocking the port, but I know firestarter will block that port automatically.  Hope this helps!

---

### Post by gagatz on 2006-02-26
Well, I don't have firestarter, is there another possibility, that ubuntu blocks this port?  And if there is, how can i disable this?

---

### Post by Sandlst on 2006-02-26
AFAIK ubuntu will not block any port just by itself-I would think, therefore, that it would be your router that is the culprit.  I would call tech support for the router-they will probobly be able to give you step-by-step instructions on making sure the ports are not being blocked by the router....hope this helps, good luck!

---

### Post by gagatz on 2006-02-26
Since I have installed the amule package with automatix, it is not possible to add any other packages with the synamptic package manager without removing amule. Why is this, and what can i do against it?

---

### Post by Sandlst on 2006-02-26
Im not sure-I've never had this problem before when using automatix, but since amule is avaliable in the repos anyway, I would install the synaptic packages you are trying to install, and when it removes amule, reinstall amule through synaptic-Im not sure if this will wipe out your configuration files for amule or not though......good luck!

---

### Post by celloandy on 2006-02-26
It's the router, not Ubuntu, that's causing your problem.  Your router is doing NAT (Network Address Translation), to route traffic from the outside to your protected internal LAN, so other amule users, servers, etc., can't directly access your ports through the router.  See [http://www.amule.org/wiki/index.php/Get_HighID](http://www.amule.org/wiki/index.php/Get_HighID) for more details.

Andrew

---

