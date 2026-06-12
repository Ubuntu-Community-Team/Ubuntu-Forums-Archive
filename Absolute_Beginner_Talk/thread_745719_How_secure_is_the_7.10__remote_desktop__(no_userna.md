---
title: "How secure is the 7.10  remote desktop?  (no username, password only?)"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2008-04-04
Hi,

I have been playing with the remote desktop software that is built into Gutsy.  I notice that when connecting (from Windows XP to Gutsy) using tightVNC that it only asks for a password.  

Is this secure enough to run on the internet?  I am using it in my internal network but I wouldnt mind having access from outside.  

Is this secure at all?

Thanks,
Rich

---

### Post by Oldsoldier2003 on 2008-04-04
> **RichTJ99 said:**
> Hi,

I have been playing with the remote desktop software that is built into Gutsy.  I notice that when connecting (from Windows XP to Gutsy) using tightVNC that it only asks for a password.  

Is this secure enough to run on the internet?  I am using it in my internal network but I wouldnt mind having access from outside.  

Is this secure at all?

Thanks,
Rich

if you use a strong password its ok i guess. I dont like it though so Ii removed vino in my gutsy install. call me paranoid...

---

### Post by RichTJ99 on 2008-04-04
Is there something else that is more secure?

---

### Post by Oldsoldier2003 on 2008-04-04
> **RichTJ99 said:**
> Is there something else that is more secure?

x over ssh using public keys...

but to be honest i rarely have a need for a remote Gui so i just ssh and do what i need.

---

### Post by Inxsible on 2008-04-04
There is also VNC over SSH to get a graphical access. Better yet, you can use NXServer which is pretty neat over SSH.

P.S I still haven't been able to successfully get thru using NXServer if I change the SSH port number. But it works great if I use the default port of 22.

---

### Post by Oldsoldier2003 on 2008-04-04
> **Inxsible said:**
> There is also VNC over SSH to get a graphical access. Better yet, you can use NXServer which is pretty neat over SSH.

P.S I still haven't been able to successfully get thru using NXServer if I change the SSH port number. But it works great if I use the default port of 22.

i dont see the big deal about changing the port. Sure it will fool some of the dumber scriptkiddies, but anyone thats determined will just port scan you. DenyHosts works just fine...

---

### Post by Inxsible on 2008-04-06
> **Oldsoldier2003 said:**
> i dont see the big deal about changing the port. Sure it will fool some of the dumber scriptkiddies, but anyone thats determined will just port scan you. DenyHosts works just fine...
Yeah, port scan does happen. but I guess it makes just a little difficult for the hacker.

But thanks for the heads up on the DenyHosts. It looks promising. I am currently reading up on it.

---

### Post by drfarrin on 2008-04-06
so on a similar subject, is it possible to controll my windows PC remotely with my ubuntu laptop?

---

### Post by Inxsible on 2008-04-06
> **drfarrin said:**
> so on a similar subject, is it possible to controll my windows PC remotely with my ubuntu laptop?
Yes you can use RDP or RDPv5 to connect to your Windows machine. Go to Applications>>Internet>>Terminal Server Client. Fill in all the details and you should be able to connect to your Windows machine.

---

### Post by RichTJ99 on 2008-04-06
Is it more or less secure that PCAnywhere?

---

