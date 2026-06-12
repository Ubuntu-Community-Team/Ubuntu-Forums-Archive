---
title: "VBox: Ubuntu Host, XP guest Host-Only Issue"
date: 2012-08-28
forum: Any Other OS
---

### Post by jbuczek on 2012-08-28
Running Linux Mint 13 (aka Ubuntu 12.04 w/ Mate) and Virtualbox from the repositories.  WinXP is the guest.

I need this VM only for TurboCADD V15.2. I want to keep the VM as small and clean as possible so that I will never have to do another XP install again... in part because I worry about "activation" after MS drops all support for XP next year.  When everything is exactly right I'll clone the VM to a DVD and hopefully be set for life even if the HDD fails.  I may even buy one of those "glass" DVD's that guaranteed for 100 years.

I DON'T want web access for the VM mostly because I don't want to deal with VM firewall/virus protection issues.

I DO need to print to the hosts cups printer (HP2060 w/ HPLIPS).

I first set up Vbox networking as "bridged". Printer and shared folders  work fine but the VM is exposed to the web. 

I've been trying to connect the VM to the host's printer via VBox "host-only networking" but I can't make it work. I can ping both ways but when I try to connect the printer XP can't see it.  I'm guessing the problem is because the "host-only" link is a different subnet.

Is there any way to set up so the printer is accessible to both nets?  I'm guessing this means making it visible to two nets at the same time possibly by masking.  By default VBox puts the host-only link in the 10.x.x.x space and my LAN is on 192.168.2.x. I could change either if necessary: i.e.:  X.X.2.X and X.X.3.X but I don't know if this can be done via masking or should it be done via cups, i.e. can I set up one physical printer as two cups printers with a common queue?

It's been 15 years since I did much networking and the info is just not in my head any more and two days of googling hasn't helped.  Anyone out there know if this can be done?

TIA

---

### Post by OM55 on 2012-08-28
Hello jbuczek,

You should be able to achieve this setup using a Samba server on the Linux host, and sharing the host's printer. There is no need to specifically make the printer visible on 'two networks' since the Samba Server will easily share the printer on any network local to the host, like any other network server.

You can install Samba from the repositories using Software Center or:
```
sudo apt-get install samba
```Then open the graphic Samba interface and set up the share for the printer. Give it a short share name and without spaces (Windows XP is limited in the length of a share name and have problem with spaces in the name).

[I][By default this shared printer will be visible to all other computers on the local network. If you want to limit access only to the XP Virtual Machine, you can define that in the Samba utility (very limited) or in the configuration file (very comprehensive, you may need a text manual).]
[/I]
When done, launch your XP virtual box and set up a _**network printer**_. You can also run the 'network printer search' feature, it should be able to find the shared host printer, and you will be good to go.

Hope that helps!

---

### Post by Perfect Storm on 2012-08-29
Moved to Other OS/Distro Talk.

---

