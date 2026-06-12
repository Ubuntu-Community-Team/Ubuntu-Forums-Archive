---
title: "Replace Windows with Linux"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by henkdeswardt on 2005-12-05
I want to propose to my company to replace all our PC's operating systems with Linux.

In order to do this proposal, I first need to get all my facts together. To do this, I would appreciate help on the following items:

1) Training: Where can we get training for myself as the Network Admin. I know very little about Linux. I need to be trained enough to admin a Server and network (about 20 PCs) and to be able to train and help the other users.
2) Hardware: How do I find out if Linux will support the hardware? Starting from a P2, P3, P4, AMD K7, K8, 64+. Raid controllers, PCI-Express screen cards, Hp printer, Ricoh printer, etc.
3) Replace software:
        Anti-Virus,
        Office software: To replace Word, Excel, Power Point, Access, Outlook,
        Fax software: To replace RelayFax: Centralised PC based faxing
        etc.

Your assistance will be much appreciated.

Henk de Swardt
Technical Manager
ArmCoil Afrika

---

### Post by nocturn on 2005-12-05
[QUOTE=henkdeswardt]I want to propose to my company to replace all our PC's operating systems with Linux.
[/quote]

I wish you all the best in this!

> 
1) Training: Where can we get training for myself as the Network Admin. I know very little about Linux. I need to be trained enough to admin a Server and network (about 20 PCs) and to be able to train and help the other users.


Canonical offers support and maybe training, you can try to contact them.
If you can find a good training in your area, but for a different distro, you can still use what you learn there on Ubuntu.

But remember to take it easy, take on one thing at a time (for example, first the mail server, once that is complete, the webserver).

> 
2) Hardware: How do I find out if Linux will support the hardware? Starting from a P2, P3, P4, AMD K7, K8, 64+. Raid controllers, PCI-Express screen cards, Hp printer, Ricoh printer, etc.


Most older hardware will work fine (all processors are supported).
For the others, make an inventory and use google or post here to check for support.

> 
3) Replace software:
        Anti-Virus,


The only place where this makes sense on Linux is on your mailserver.  Look at mailscanner for this, it integrates SPAM/Virus and other cleaning and is very nice.

> 
        Office software: To replace Word, Excel, Power Point, Access, Outlook,


Ubuntu 5.10 comes with OpenOffice 2, which is in my opinion much better then MS Office.  It can replace the above and can also open most MS files.

> 
        Fax software: To replace RelayFax: Centralised PC based faxing
        etc.


I know solutions like this exist, but I have never used a fax, so this is beyond me.  

> 
Your assistance will be much appreciated.


No problem, you can always ask about specific problems you have during the migration here, we will be happy to help.
Henk de Swardt
Technical Manager
ArmCoil Afrika[/QUOTE]

---

### Post by henkdeswardt on 2005-12-05
Are there not a training institution for Ubuntu?

I heard Ubuntu might not be the best distro for the Server, but I would prefer to support the local guys.

Henk de Swardt

---

### Post by Jonne on 2005-12-05
I'd suggest to first try running Ubuntu on your own computer (I'm assuming you're in no hurry to switch over here), before converting every computer in the company. Switching over servers can be done without many problems either (unless it's a domain controller or something).

You could also start switching programs gradually, a lot of Open Source software runs on Windows too. Install OpenOffice.org, Firefox, Thunderbird, etc... under Windows, and once you're ready to switch the OS, the people probably won't notice, as they'll have the same apps.

Get the Ubuntu liveCD, and you'll be able to test hardware compatibility for every computer just by booting it with the cd in the tray.

Contacting Canonical might be a good idea too, like Nocturnal said. I'm sure a support contract is cheaper than all software licenses you probably pay for now.

---

### Post by Hendry on 2005-12-05
[QUOTE=henkdeswardt]
1) Training: Where can we get training for myself as the Network Admin. I know very little about Linux. I need to be trained enough to admin a Server and network (about 20 PCs) and to be able to train and help the other users. [/QUOTE]

I know Novell (Suse) and Redhat offer Linux training. Information you can use then on the distro you are going to use as a server

---

