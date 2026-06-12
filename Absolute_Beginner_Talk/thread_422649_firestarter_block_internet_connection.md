---
title: "firestarter block internet connection"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by te.ss on 2007-04-25
Hi, everyone. 

I finally took a tiny first step into the Ubuntu /Linux world from the Window world.  So far, I'm pleased except ...

Feeling a bit uncomfortable while browsing webs (this is a Window user thing), I installed firestarter.  I just let the wizard run.  After the installation I can no longer connect to the internet unless I  disable firestarter.  And the firestarter runs automatically when I boot-up.  
What did I do wrong (or did not do)?  

When I did <sudo iptables --list>, there's nothing.  Is this the way at the beginning?

---

### Post by u.b.u.n.t.u on 2007-04-25
From memory, Firestarter has it's own GUI. 

When you say you cannot connect to the net, is that one program like Firefox or everything such as Synaptic and update the time via an atomic clock?

Perhaps Firestarter was over zealous. If you can't find the GUI, it won't hurt to reinstall Firestarter and watch it more closely this time.

---

### Post by u.b.u.n.t.u on 2007-04-25
From my own wiki link below, from Ubuntu 6.06:

:)


Firestarter (Firewall GUI for iptables.)

* Check to see if Firestarter is running.
sudo /etc/init.d/firestarter status


* Add Firestarter to start-up programs.
System > Preferences > Sessions
Click.
Add
Enter the text.
sudo firestarter --start-hidden

---

### Post by mikeyphi on 2007-04-25
Firewall - somewhat complex!!
If you insist on installing perhaps you might try the Firewall builder GUI available through synaptic. I haven't used it but the book says that it provides a simple(!!) method for setting up your Firewall

---

### Post by te.ss on 2007-04-25
Thanks u.b.u.n.t.u.  I tried a reinstallation and also added a firestarter in the start-up.  
But still no connection as far as the firestarter is active.  Absolutely no connection - firefox, evolution.

I'd better deactivate / remove firestarter for now, it seems.  I assume it's still fairly safe, isn't it?

---

### Post by oilchangeguy on 2007-04-25
firestarter is NOT the firewall. ubuntu's built-in firewall is called iptables. and firestarter is nothing more than an un-needed control panel for iptables. if you'll let ubuntu do it's thing you'll be fine. i'm not sure how to go about un-doing the changes you've made using firestarter. try to change back whatever you've done and uninstall firestarter.

---

### Post by te.ss on 2007-04-25
Thanks oilchangeguy.  
I removed it and worked fine.  I guess I just get used to the idea that iptables is taking care of the security quietly.  It's a big leap for a window user.

---

### Post by te.ss on 2007-04-25
Thanks mikeyphi.
I removed it and am happy surfing the web and reading emails.

---

