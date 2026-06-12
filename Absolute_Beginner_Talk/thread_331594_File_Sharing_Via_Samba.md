---
title: "File Sharing Via Samba"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Fingerz91 on 2007-01-04
Hello All!

I just wanted to say thanks for helping a new Ubuntu user, I can now say that I am typing this from within a Ubuntu Edgy system and have my ATI card up and running! However, One computer at my business uses Linspire 5.0 and uses Samba to share files. I have configured both the Ubuntu and Linspire system to the workgroup mshome and when I browse the network I see nothing. I do not use a firewall on Ubuntu and Linspire's firewall is set to Open To Local Network.....

I am not sure what is going on, but I am sure you guys can help!

---

### Post by tzulberti on 2007-01-04
Sorry, but i am a little confused. You are using Samba to connect 2 PCs that uses Linux? IF so, you shouldn't use samba. Instead you should use: NFS...

---

### Post by jimrz on 2007-01-04
> **tzulberti said:**
> Sorry, but i am a little confused. You are using Samba to connect 2 PCs that uses Linux? IF so, you shouldn't use samba. Instead you should use: NFS...

or try SSH

---

### Post by l951b951 on 2007-01-05
I'm actually scouring the forums with the same problem.  2 linux machines and 2 Winxp machines all set up on one network.  When I browse network with Ubuntu, I can see "Windows Networks" but when I click, it is empty.  However, my Fedora Core 6 box, and both XP machines can see the Ubuntu machine, but can't access it.  I have been stumped by this - mainly because 4 days ago my samba was working perfectly and I was sharing files amongst all the machines.  
I look forward to seeing any solutions that may come up here.  My search has only brought up "How-To"s for setting up samba.  Most assume more knowledge than I have, and I have yet to get my samba to work.

---

### Post by Fingerz91 on 2007-01-05
Nevermind:p 

Got it to work....just had to edit the iptable

---

