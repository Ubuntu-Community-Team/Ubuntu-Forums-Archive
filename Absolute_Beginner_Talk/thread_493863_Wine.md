---
title: "Wine?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by fvs on 2007-07-06
'm trying to get wine to install "FilemakerPro" I have wine installed, yet when I try to install filemaler I get error message that it is not fully installed, "Change owners name in ~/.wne/system.reg? How do I do that? Thanks in advance.

---

### Post by p_quarles on 2007-07-06
Well, according to winehq.org, FileMaker doesn't have a really good success rate with Wine. It depends on which version you're using, though. Check the link to see other people's experience with different versions:

[http://appdb.winehq.org/appview.php?iAppId=337](http://appdb.winehq.org/appview.php?iAppId=337)

---

### Post by buzz40000 on 2007-07-06
For those Windows applications that don't run under Wine, you may be better off installing VMWare server and running a virtual windows machine.  I tried the Wine route with Microsoft Money and it was an exercise in frustration.

My Microsoft applications actually run better on a Ubuntu box running an XP Virtual machine via VMWare Server than they did on the same box before it was converted to Ubuntu.

I don't know the specific license VMWare products are distributed under, but it didn't cost me any cash to use VMWare Server.  There is also a VMWare Workstation and a couple of other projects, but I have no experience with them.  

Link : [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

It's really easy to use.  Start the server and create a new virtual machine.  There is a drop down list of supported operating systems, nearly all of the Windows Flavors are in there.  Choose the flavor you want.  Put the Windows O/S CD into your CD-Rom drive and tell VMServer to "power on" the virtual machine - from there it goes exactly like a regular O/S install.

I do recommend installing "VM Ware tools" once you've completed the Windows installation.  You will be prompted to do this by VMWare Server, and the process is simple (select "install VMWare tools" from the drop down menu in the VMWare Server Console).

Good Luck.

---

