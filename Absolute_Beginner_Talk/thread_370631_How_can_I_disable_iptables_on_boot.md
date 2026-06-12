---
title: "How can I disable iptables on boot?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by dpar on 2007-02-25
Can anyone tell me how I can disable iptables on bootup? I am running a hardware firewall in my router, which does a fine job. Iptables keeps throttling back my ktorrent downloads and I have to shut it off with Firestarter in order to get my download speeds up to normal again.
Whenever I reboot, it's back there turned on again.

I don't see any need for running two firewalls and the router is many times easier to configure than iptables.

---

### Post by karls0 on 2007-02-26
Hi,
I don´t have iptables running on my Kubuntu-box and I have a german version, so some names might differ a bit, but I think you will know what I mean. In my opinion there are two ways to do this.

Go to K-menu, systemsettings. Way down in systemadministration you will find systemservices or services (with the traffic-light icon). Search for iptables and disable "start at bootup".

Usually services are startet by script in /etc/init.d/, but not directly. For each runlevel there is a directory named i.e. /etc/rc2.d/ for runlevel 2. These directories contain symbolic links to the startscripts in /etc/init.d/ with names that start with "S" and a number, which gives the startup-order. 
So you could open a console (terminal) window, become root (sudo -i) and check your current runlevel (runlevel). If you get "N 2" it is two. Change to  the corresponding directory (cd /etc/rc2.d) and list its content (ls -l). If you see a line containing something with iptables, you got it. Since you never know if you will need it again, I rename the link, so that it doesn´t get called any more (mv S23iptables _S23iptables). You can name it to your like, but you have to make sur that it doesn´t beginn with an "S".

hth
Karl

---

### Post by dpar on 2007-02-26
Hi;
Thanks very much, this looks like what I need. I'll try out your suggestions when I get home from work.

Thanks again

---

### Post by OffHand on 2007-02-26
You can also ignore it because it doesn't do anything by default.

---

### Post by dpar on 2007-02-26
What doesn't do anything?? iptables? Because when I shut it off with Firestarter, my download rates imediately jump from 10kb/sec to 170kb/sec. I'd say that would indicate it does something.:)

---

