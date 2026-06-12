---
title: "Can You Log In to Windows from Linux"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by elesh on 2007-01-21
Here is my dilemma: I want to use Ubuntu full time in my office. However, there are some applications which require windows.

Currently I think my option is to create a dual boot system.

However, is it possible to log into a windows system from linux and use windows 
applications?

Would this be done with VPN?


I appreciate any guidance.

---

### Post by Shatrat on 2007-01-21
What applications are you talking about?
If you already have a windows CD key then you might as well set up a dual boot system, but depending on the applications you need you might be able to run them in wine.
Search for them at appdb.winehq.net to get an idea of how well they run in wine or if they run at all.

---

### Post by zerhacke on 2007-01-21
> **elesh said:**
> Here is my dilemma: I want to use Ubuntu full time in my office. However, there are some applications which require windows.

Currently I think my option is to create a dual boot system.

However, is it possible to log into a windows system from linux and use windows 
applications?

Would this be done with VPN?


I appreciate any guidance.

With a dual boot system you can log in to either Windows or Linux at boot time.  If you're in Linux and need a Windows app, you shut down the computer, reboot, and select Windows in Grub.  Or, see if your program will run in WINE as suggested above.

However, when you are booted into Linux, you cannot issue a command to start Windows short of rebooting.  Windows can't be started while inside of Linux.  Likewise, Linux cannot be started while in Windows.  You have to reboot and choose the OS in GRUB.

---

### Post by elesh on 2007-01-21
The program is called remote view. It allows access to a a DVR security camera. You can view live, or record, etc.

I dont see this program on the wine appdb; 
Can I using this application with linux/win even if its not supported?

Also I would like to rephrase my question:

In general, is it possible to VPN into a windows desktop from linux?
What I am thinking of doing is setting up a server with windows applications
and using Linux Desktops at work. When a windows application is required, I want them to be able to access those programs from the Windows server.

I don't now how possible all this is, but I suppose its my end goal (which can be modified 
as I recieve advise)

Thank You again

---

### Post by Tomosaur on 2007-01-21
Even though the application is not listed in AppDB, it'll still do no harm at all to try it out. If it works, just submit it to the AppDB.

Failing that, yes, it is possible to run Windows through Linux (ie, as a program you load from linux). You need to look into [VMWare](http://www.vmware.com/). I have never used it so I don't know how well it works, but it's supposedly very good. Worth a go anyway.

---

### Post by Shatrat on 2007-01-21
I think what you are talking about is VNC and I don't have any experience tinkering with that personally, although I think it might be a little laggy for viewing video from security cameras.

It's certainly worth a try.
You could install [http://www.realvnc.com/products/free/4.1/winvnc.html](http://www.realvnc.com/products/free/4.1/winvnc.html)
on a windows machine and then use a vncviewer to connect to it in ubuntu.

My curiosity is piqued, I think im gonna play around with it a bit now.

---

### Post by elesh on 2007-01-21
Okay this definately points me in the right direction.

Thank you Tomosaur, Shatrat.

---

### Post by Sutekh on 2007-01-22
You can also try [PPTP]("http://pptpclient.sourceforge.net/howto-debian.phtml") to connect to a Windows VPN.

Try this for connecting in Ubuntu Edgy.

           [VPN Connection in Edgy]("http://customisinglife.wordpress.com/2006/11/20/vpn-connection-in-edgy/")

Or try these for PPTP and remote desktop connections from Ubuntu (Dapper) to Windows ...

           [Access Microsoft VPN Using PPTP]("http://customisinglife.wordpress.com/2006/10/17/access-microsoft-vpn-using-pptp/")

            [Remote Desktop to a Windows Machine in Ubuntu]("http://customisinglife.wordpress.com/2006/10/23/remote-desktop-to-a-windows-machine-in-ubuntu/")

Good Luck!!

---

### Post by steve.horsley on 2007-01-22
If it's a recent version of Windows, it can probably also be controlled from another Windows box. The protocol is called Remote Desktop Protocol, I think. If so, then you can use a Linux application called rdesktop to control it from Linux (in Ubuntu, menu Internet -> Terminal Server Client and choose RDP protocol). RDP is faster than VNC, and seems to work rather better in my view.

---

### Post by Josh1 on 2007-01-22
Either use:

1) WINE - To run the programs you want to use that only run in Windows
2) VMWare - Run Windows XP within Ubuntu, very handy sometimes
3) Dualboot

---

