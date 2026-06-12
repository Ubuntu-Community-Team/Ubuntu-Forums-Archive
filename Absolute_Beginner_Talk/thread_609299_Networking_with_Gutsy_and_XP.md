---
title: "Networking with Gutsy and XP"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by prcm311 on 2007-11-10
I realize that I could probably find the answer to my networking problems if I searched these forums more, but I've spent about a week on this and I'm no closer than I was before.  Here's my dilemma:

I have three computers on my home network:  aaron-desktop (Ubuntu 7.10), april-laptop (Ubuntu 7.10) and april-windesk (xp pro sp2).  All of these machines dual boot both Gutsy and XP, I've listed the default OS of each.  I've just recently installed (new install, not upgrade) Gutsy into all three machines and loaded Samba and NFS.  Two have content shared using Samba (WINS is checked), the XP machine has simple sharing disabled and is sharing content as well.  All computers belong to the same workgroup, MSHOME.

The Ubuntu machines cannot see each other or my windows machine.  My windows machine can see my linux ones but cannot access them.

I am looking for a solution to this that allows me to use Samba from my linux boxes.

All machines are setup with static IPs.  I have a standard Netgear router, with standard cable internet service.  All computers are able to access the internet and ping each other.

Any help would be greatly appreciated.

---

### Post by Daveski on 2007-11-11
My suggestions would be:
Have you checked firewall settings?
I would remove the WINS setting.
Have you waited the 15 minutes that it can take the Windows File and Printer sharing system to display all networked systems?

---

### Post by prcm311 on 2007-11-11
Yes, I have checked all of those settings.  WINS being checked or unchecked should not be causing this problem.  I've tried it both ways.  I am able to see my Ubuntu machines from Windows it's being able to access them that's the problem.

I am now able to access all my machines whether in XP or Ubuntu by typing in the IP manually.  I have also set up each OS on each machine to a static IP.  This allows me to mount the shares on my Ubuntu systems on startup.  It's a work-around though.  My goal is to use the Nautilus/Explorer GUIs to browse the network.

Is there any additional information needed?

---

### Post by Daveski on 2007-11-11
I see - that does sound like a browsing problem. If access is fine via IP then I would suggest that the master browser is not functioning correctly. Again I think removing the WINS setting on the Ubuntu machine should force it to use the peer-to-peer system of holding an election on your network where one of the machine builds the master list of resources (it is this process which can take up-to 15 minutes) which is used in browsing.

A classic way to force this is to reboot all machines on the network at the same time.

---

