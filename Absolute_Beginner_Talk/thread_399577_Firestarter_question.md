---
title: "Firestarter question"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Bobby Digital on 2007-04-02
Installed Ubuntu and I love it so far.  In fact, that is all I use on my laptop.

My only problem so far is with Firestarter.  When I open the application is shows that it is enabled and running and I also get the tray icon.  The tray icon stays after I close it.

However, I cannot get the tray icon on boot (my Windows paranoia forces me to have visual confirmation that the firewall is running). 

Any ideas?

---

### Post by kinematic on 2007-04-02
the tray icon is completely unnessecary.
firestarter is just a graphical frontend to configure iptables.....iptables is the firewall build into the linux kernel and is ALWAYS running.
just sit back and let go of your windows worries ;-)

---

### Post by johnc4510 on 2007-04-02
Firestarter is only the graphical interface for the real firewall iptables. It enables you to configure the firewall without having to use the terminal interface. You really don't have to have it running all the time. However, you can make it run at boot I believe by adding it to your start programs.

System>Perferences>Sessions

Click on Startup Programs Tab

And add this:

gksudo firestarter

---

### Post by Bobby Digital on 2007-04-02
> **kinematic said:**
> the tray icon is completely unnessecary.
firestarter is just a graphical frontend to configure iptables.....iptables is the firewall build into the linux kernel and is ALWAYS running.
just sit back and let go of your windows worries ;-)

Thanks for the replies.  

I will try.  Windows has trained me to scan with 8 different virus/spyware scanning tools and constantly port scan my machine for open ports.  Plus, I can't forget about Patch Tuesday!

It's hard to get used to turning on your computer and doing................work.

---

### Post by kinematic on 2007-04-02
that just presents him with a permissions box just as he would get if he wants to configure iptables.

---

### Post by kinematic on 2007-04-02
> **Bobby Digital said:**
> Thanks for the replies.  
It's hard to get used to turning on your computer and doing................work.

i know what you mean...that's exactly how we felt when we started to use gnu/linux.

---

### Post by johnc4510 on 2007-04-02
kinematic:
Yes, but then all you need to do is close the gui and the tray icon should stay.

---

### Post by airtonix on 2007-04-02
if you want visual confirmation of network activity use either of these two methods : 

1. system-monitor applet in the gnome panel...(turing on network graph by right clicking the widget and selecting preferences.)
this will show you network activity, and over time you will get an understanding of what to expect.

2. install htop and jnettop. run them in the terminal and possibly swallow them into the gnome-panel with : gnome-swallow-applet

open a terminal and type : 
> sudo apt-get install gnome-swallow-applet htop jnettop
enter your password and then when that is all done and back at a pending prompt press : ctrl+shift+t  to open a new tab in gnome-terminal

 then type : 
> sudo jnettop -i eth0

and open another tab again then type : 

> sudo htop

hope that helps you.

---

