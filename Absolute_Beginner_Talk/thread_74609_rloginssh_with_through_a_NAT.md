---
title: "rlogin/ssh with through a NAT ?"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-12
rlogin with a Nat
  
Hi Linux Community, 
  
  
That's my very difficult question:
  
 
I would like to do rlogin or ssh from outside my network. 

PC2 ====> Internet =====> NAT(69.x.x.x) ==========> PC1 (10.x.x.x) (Linux)

I would like to access to my PC1 from my PC2.
Is there a way to do so ?

I tried wity xterm (rlogin & ssh) and putty too (wine) to log via ssh and rlogin 
to my IP_NAT_Address_69.x.x.x  

I dont have access to any port forward or configuration, i guess the port ssh 22 is open. I cant do any port forward

I also tried to log there : 69.x.x.x:10.x.x.x      via ssh but of course, not workign 
I saw that in putty, there is some stuffs concerning tunneling ... 
But I dont know the use.
  
Is there a way to access my Linux from PC2 ??

thank you very much,
  
(I am rather sure that there is possibilities or programs)
(a third pc maybe in between)

Patrick

---

### Post by wombat20 on 2005-10-12
Not done it myself (yet), but have a look at the guide:

[http://www.ubuntuguide.org/#sshserver](http://www.ubuntuguide.org/#sshserver)

---

### Post by patrick295767 on 2005-10-12
[QUOTE=wombat20]Not done it myself (yet), but have a look at the guide:

[http://www.ubuntuguide.org/#sshserver](http://www.ubuntuguide.org/#sshserver)[/QUOTE]

Thank you very much, 

I 'll read it in detail about ssh ...
I had already a quick look but i guess it wont help to read the PC IP_10.x.x.x
I will ONLY see the NAT... Unfortunatly

thank you 

Patrick

---

### Post by mlomker on 2005-10-12
> I had already a quick look but i guess it wont help to read the PC IP_10.x.x.x
I will ONLY see the NAT... Unfortunatly


It can't be done.  SSH is a secure protocol and therefore cannot be used over a NAT.  You'd have to VPN into the firewall/NAT device and establish a tunnel for it to work (that avoids the translation).

---

