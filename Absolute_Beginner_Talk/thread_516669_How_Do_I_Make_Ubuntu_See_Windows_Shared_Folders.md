---
title: "How Do I Make Ubuntu See Windows Shared Folders"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by kpurcell on 2007-08-03
Subject says it all.

I have a laptop with wifi getting DNS from my linksys wrt54g router. 
I have an XP Home desktop with multiple shared folders.

I have tried to go into Places-- Network and it finds the Windows network and then I double click and it sees my workgroup name.  But when I double click that it gives an error message saying "The folder contents could not be displayed"

---

### Post by scrooge_74 on 2007-08-03
Check this [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

hope it helps

---

### Post by kpurcell on 2007-08-03
Thanks, but unfortunately I tried to follow that guide and it did not work for me.

---

### Post by misconfiguration on 2007-08-03
kpurcell,

I think you need to install the samba application as well as the samba front-end.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Many thanks to Stormbringer for writing this tutorial. 


Hope this helps, mate!

---

### Post by ugm6hr on 2007-08-03
Xubuntu doesn't have the Network/Places feature - so I use pyNeighborhood.  It works just as well in Ubuntu.

Have a look at the link in my signature (Easy Windows file sharing) if you want to give this a try.

---

### Post by kpurcell on 2007-08-06
OK
To Misconfiguration:
I clicked your link on isntalling Samba and it says
1. Prerequisites 
- Your Linux box should have an static ip-address.

Thats a deal breaker.  If I cannot browse my network using DHCP then I can't use Ubuntu.  is there some other way to configure it?

To ugm6hr
I am not using Xubuntu.  I'm using regular Ubuntu and don't have the xubuntu-system-tools.  I went to install them and it says it conflicts with gnome tools.  So is there some other way to make it work.

thanks for your help, but this is still not working for me

Just so you know my setup if it is needed.
I have a Linsys WRT54G set up giving my systems their IP via DHCP. I have to do this so that my phone works.  It requires it and won't work any other way.  I use vonage.

Have an Emachines desktop with XP Home sharing folders and a printer.  I have another printer that is directly hooked to the router and is a network interface printer.  Brother provides no linux drivers for it so I am sure I won't be able to print to it.

I am imply trying to access a folder that is shared as "backup" on the D drive of my XP box.

---

### Post by ugm6hr on 2007-08-06
> **kpurcell said:**
> 
To ugm6hr
I am not using Xubuntu.  I'm using regular Ubuntu and don't have the xubuntu-system-tools.  I went to install them and it says it conflicts with gnome tools.  So is there some other way to make it work.


Sorry.... I never really edited properly for Gnome users....  

You don't need to install anything other than pyNeighborhood to get this to work.  Everything else is already installed (or will install when you activate shared folders).  I have not tried it in Gnome Ubuntu - but someone else has... I will try and retrieve that post so you can see for yourself...

EDIT: Here it is [http://ubuntuforums.org/showthread.php?t=500770](http://ubuntuforums.org/showthread.php?t=500770)

---

### Post by kpurcell on 2007-08-07
ugm6hr
Thanks for trying but I see nothing new here.  The link you have is people discussing making it work following the original link you gave.  As I said I don't have Xubuntu.  You said I don't have to install anything.  Fine.  I only installed pyNeighborhood, but it does not work still.  I can see my machine but when the box opens asking for IP address I try to get it to retrieve this info and it won't..  As I said, I have DHCP working and so the IP address will change possibly.  But I entered the current IP address and now I can see the machine and the shared folders.  But when I click on them it says "Failed to mount"

---

### Post by rsnow on 2007-08-07
I just completed accomplishing this very thing (thanks to the help of P. Quarles) and here is the link to all the that I went through. I think the last page is where we finally figured out what needed to be done.

[http://ubuntuforums.org/showthread.php?t=513282](http://ubuntuforums.org/showthread.php?t=513282)

---

### Post by ugm6hr on 2007-08-07
> **kpurcell said:**
> ugm6hr
Thanks for trying but I see nothing new here.  The link you have is people discussing making it work following the original link you gave.  As I said I don't have Xubuntu.  You said I don't have to install anything.  Fine.  I only installed pyNeighborhood, but it does not work still.  I can see my machine but when the box opens asking for IP address I try to get it to retrieve this info and it won't..  As I said, I have DHCP working and so the IP address will change possibly.  But I entered the current IP address and now I can see the machine and the shared folders.  But when I click on them it says "Failed to mount"

One last try - then I promise I'll leave you alone.

How did you run pyNeighborhood?  If you selected it from the menu entry - it will not work (as explained in the thread).

You need to run it with:
Alt+F2: **gksudo pyNeighborhood**

This is why I have created a custom panel launcher for pyNeighborhood.  Of course - you could just edit the menu entry...

And the point of the new link was just to show that it does work in Ubuntu (and not just Xubuntu).

But.... since then, I stumbled across this - which looks pretty easy too:
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

