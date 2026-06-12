---
title: "network configurations, other questions.."
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by juanzo007 on 2008-01-07
Hi folks...  Brand new to linux, just got installed and figured out how to add applications.  I'm fascinated by all of this, but i'm not sure how to best configure my new ubuntu box in my network.

I have 1 hp media desktop, win xp, intel core duo, 2GB ram
1 xp laptop
ubuntu box 2.4Ghz pentium 4, 728mb ram, 120gig HD.
trendnet g wireless router.

Q #1.  My original intention was for it to be a file and print server and autobackup my important work and personal files.  but i'm not finding a clear method for networking with win xp.  Any suggestions for finding a layman's explanation?

Q #2.  The internet connection is lightning fast with unbuntu, and apparently is more secure.  Given that, can i set up my network to have the ubuntu box be a firewall for the whole network, use it for my browsing, and be my file server, while allowing my desktop and laptop to run my needed windows applications?  Do i need a firewall/ AV applications?  

Fantastic stuff.  If anyone could point me in the direction to educate myself or share any networking configuration ideas, it would be much appreciated.

---

### Post by reckless2k2 on 2008-01-07
question 1: i believe you need to look up SAMBA as far as having your windows box talk to your linux box. there is samba connection applications in add/remove programs in ubuntu. 

question 2: you can make your linux box everything and just about anything really. there are specific versions of linux that act as a firewall and content filter and all that good stuff. tweaking you ubuntu box up to do that will require a lot of command line tweaks. i wouldn't recommend it in general especially because your router more than likely has a firewall in it now. you only need AV on ubuntu if it's serving windows boxes. ubuntu has a builtin firewall already. now you do need all that good stuff on windows no matter what though even if you have a firewall or AV somewhere else on your network. 

educational away:

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

enjoy

---

### Post by juanzo007 on 2008-01-07
Thanks much...  Samba, yes...

Let me ask if this makes sense.  If i spend most of my time surfing for info and email, and using my hp box for Office apps and the like, would i want to set up up my ubuntu box as the network host and run my xp box from it remotely for my apps?  

And in general, how secure is ubuntu with remote access - say i need to access a file from there while out of the road?

Thanks again!

---

### Post by reckless2k2 on 2008-01-07
ubuntu/linux in general is designed for that purpose with security being on the forefront. depending on "how" you want to access the linux box remotely (command line or GUI), it's not very hard. 

did you plan to run serves across the internet? like if you need to just access some files you can do it through FTP or secured http. there are various ways to do things. ubuntu would only be the server in your network with hardened security. think about it like that.

eval the services you want, like, or need and PM me. i should be able to help.

---

### Post by juanzo007 on 2008-01-07
Many thanks...  I'll do some of my own homework and tinkering, but i may take you up on some advice...

---

