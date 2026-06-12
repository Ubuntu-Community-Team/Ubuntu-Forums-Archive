---
title: "Installing HP LJ 4250 in Xubuntu 7.04"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Curbuntu on 2007-08-18
I've been playing with a new install of Xubuntu on an old Toshiba laptop,  Despite the P-II processor and 96 Mb of memory, it works remarkably well.  I haven't tried my wireless card (a Linksys WPC11) yet, but it's on the network and the 'Net with its wired network card (an old 3Com PCMCIA).

Xubuntu's printer setup routine even found the printer here, an HP LaserJet 4250 on the network with an IP address of 10.19.52.9.  It looks like it set up properly as the default (and only) printer, but it won't print a test page.

Obviously, I need to learn the ins and outs of *buntu printer setup.  Some of the problem, no doubt, is that I don't understand what a "socket" is (part of the "URI"), nor do I know why that socket is associated with port 9100.  Those were things the printer setup routine added by default.

The newbie awaits some guru's enlightenment...

---

### Post by Curbuntu on 2007-08-18
> **Curbuntu said:**
> Obviously, I need to learn the ins and outs of *buntu printer setup.  

Well, before somebody decided to give me the RTFM message, I went to the Xubuntu.org page on printing and printers.  Unfortunately, what it says to do there doesn't match the reality of what I find in Xubuntu 7.04.  Consider the instructions under printing on a network:

> **Printer Configuration with the Browser**

First, you will need to enable the web administration interface of CUPS 
(Common UNIX Printing System).

1. Launch Applications->System->Users and Groups, click on the tab Groups, and check Show all users and groups

2. Select the group shadow and click Properties.

3. Add the user cupsys to the group.

Now, maybe this doesn't apply, even though the printer stands alone with its own IP address on our network.  (I mean, perhaps this only applies to a printer on a full-blown printer server.  Hey, they don't call us "newbies" for nothin'!)  I can make my way to Applications | System | Users and Groups well enough, but it breaks down on the next step.  There is no "tab" called **Groups**.  In fact, there are no tabs at all, just a two-line list with yours truly as user and as "root."

There is a *button* that says "Manage Groups," which brings me to a "Groups settings" dialog box; but there is no "shadow" group in that list.

FWIW, I also noticed that both of my listing appear in every group, but (with the exception of one listing in one group) none of the boxes are checked.

---

