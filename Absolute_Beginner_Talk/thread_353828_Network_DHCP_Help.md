---
title: "Network DHCP Help"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by orcalover on 2007-02-05
Can someone point me in the right direction regarding setting up a local area network for my home office. I want one PC to act as the server/domain controller, and enable users to login at any computer (since their accounts will reside on the server) and have access to their documents, etc from all computers. 

Also, I have two nic cards on my PC (the one that will act as the server) and it seems as though eth1 is the connection to the internet (connected to the router), and eth0 is the connection to the local area network (connected to my switch). From everything I have read, this seems to be setup backwards. I should note that the physical cable connections have not changed since I removed the Windows Server and installed Ubuntu, so I know that the cables are connected to the right nic card, etc. Is this going to be a problem?

Thanks
Sean

---

### Post by Ben Sprinkle on 2007-02-05
Well the networks should be recognized automatically. To add a folder for sharing on it:
1. Click System > Admin > Sharing folders
I belive, then to view:
1. Click Places > Network Servers

---

### Post by orcalover on 2007-02-05
Well, I haven't setup the server at the moment, this is what I'm needing some help on. 

I am going to assume that I need two domain names, one local (domain.local) for the intranet, and one internet domain (domain.com) for the internet site, correct? Or, is the local domain only needed for windows networking?

Also, how do I setup the server so that users can login from any computer with their login, and have their documents, etc, stored on the server?

Trying to figure all this out, but again, I'm lost. 

I think I fixed the eth0 and eth1 issue, but I'm not sure yet. 

Sean

---

### Post by Ben Sprinkle on 2007-02-06
???
Not for local lan...

---

