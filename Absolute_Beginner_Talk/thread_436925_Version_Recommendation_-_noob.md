---
title: "Version Recommendation - noob"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by scm910 on 2007-05-08
Hello!

I have a 4 year old Dell P4 that I want to convert into a Linux Server.  My primary objectives with this server are (in order of priority):

**1) Backup** - I want to back up files across the network from a windows desktop pc, an apple powerbook, and a windows laptop to a 400GB USB HardDrive.  I would also like to do a single offsite backup from the server periodically.
**2) Print Server** - I want to share 3 printers across my network.
**3) Media Server** - I want to store my media files (music, video and photos) in a central location that is accessible from all of the above-referenced computers on my network.

I searched the forums already and found some good info but nothing that applies specifically to my situation.  I have a feeling you are going to tell me to install Edgy since I really don't need the hardcore server/client functionality of Dapper (nor will I ever need my own web server in my home office).

Additional Info: I have Brighthouse Roadrunner residential broadband (cable) and a Netgear Wireless Router (4 ethernet ports).  I prefer a GUI but I'm not afraid of the command line and think I could pick it up quickly enough.

Thanks in advance for everyone's consideration and effort.  I am looking forward to learning as much as I can about Ubuntu!

-Steve M
Orlando, FL

---

### Post by PriceChild on 2007-05-08
I would say Dapper or Feisty. There's no reason for edgy imo as if you want real stability you go dapper, if you want latest versions you go feisty.

---

### Post by hyper_ch on 2007-05-08
If  it's just for that reason I'd rather go with a debian server install... a gui will only slow it unnecessarily down...

---

### Post by kebes on 2007-05-08
I agree with PriceChild, either install Ubuntu 6.06 LTS (Dapper Drake) or Ubuntu 7.04 (Feisty Fawn).

Dapper is a "Long Term Support", which means that it is very stable, and will continue getting bugfixes and security updates for many years. This is what I use for servers (web servers, file servers, media boxes, etc.) since it is very stable and reliable. It should fully support your hardware.

Feisty is the "brand new" version, and it includes all the "newest technology". It is also stable and is great as a desktop, since the newest versions of software are immediately available for it.


So, really, each would be a great choice. Both will have all the software you need to do what you want. But, since you won't be using the box as a desktop machine, I guess I would say that Dapper is a slightly better choice, since it may be a ~bit~ more stable.


Once you've chosen a version, you can either install the "server version" or the "desktop version." They are really very similar, except that the "server version" doesn't have a GUI in the default install (but you can add it easily). Similarly, it's very easy to add the server packages to the desktop version. Typically, for a home server, I just use the desktop install.

Hope that helps!

---

### Post by jiminycricket on 2007-05-08
Have you looked into **[BackupPC ]("http://www.tuxmachines.org/node/12887")**for your backup, or what are you using, just for my own curiousity?

---

### Post by scm910 on 2007-05-08
I sincerely appreciate all of the feedback.  I've decided to go with Desktop Dapper for stability purposes and the GUI will be a major benefit is someone besides me needs to operate the server (no one else in my circle has ever seen the command line).

jiminy,
I just cruised over to BackupPC and it seems like something I will check-out in greater detail.  For the PC, I am using Cobian Backup 8 and for the Mac I was planning on using SuperDuper.

I'll post some results here soon.  Plus, I'll probably trip over myself a few times during the set-up and will need more assistance.

Thanks again.

---

