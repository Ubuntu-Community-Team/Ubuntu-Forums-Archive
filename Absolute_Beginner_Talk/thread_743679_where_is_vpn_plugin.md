---
title: "where is vpn plugin?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by hanenming on 2008-04-02
Absolute beginner..want to install vpn, read that I need a vpn plugin...where do I get that?

---

### Post by ghost_ryder35 on 2008-04-02
> **hanenming said:**
> Absolute beginner..want to install vpn, read that I need a vpn plugin...where do I get that?


Have you tried "Add/Remove Applications" under Applications button on the top toolbar next to places.  just search for "VPN"  its in there

---

### Post by hanenming on 2008-04-03
well, did the search in Add/Remove under Applications, nothing...  but I did manage to install the pptp-linux plugin, but still no option for VPN when I left-click on Network Manager,  all I get is "Manual Configuration..."

---

### Post by Xiong Chiamiov on 2008-04-03
I see a few plugins when I search for VPN, so it's likely you don't have the proper repositories enabled.  Take a look at [this]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096").

---

### Post by hanenming on 2008-04-03
ok, activated all repositories..found and installed vpn software, but still, no vpn option in network manager on left-click...do I need to reboot to have the new vpn software take effect?

---

### Post by Xiong Chiamiov on 2008-04-03
Possibly.  I haven't used VPN at all, but rebooting can do wonders for a computer problem.

---

### Post by hanenming on 2008-04-03
okay, computer restarted, still no vpn option.  I'd read in some threads about vpn not being available with static IP.  I don't know what that means, or if it applies to me...any clue?

---

### Post by Xiong Chiamiov on 2008-04-03
A static IP is when your router always assigns the same IP address to each computer, rather than assigning the next one available at the moment.  If you don't know about it, you probably don't have it set up.
As for your problem, I'm not really sure.  Sorry.

---

### Post by hanenming on 2008-04-03
Thanks anyway...I went back into Package Mgr and installed several different vpn options (openvpn, and some others), and according to other threads, I should be presented with the option to setup VPN on left-click (network mgr)...but alas, no change :confused:

---

### Post by hanenming on 2008-04-03
okay, found a site that said to enable vpn I should type:
sudo apt-get install network-manager-pptp
sudo killall nm-applet
sudo /etc/init.d/dbus restart
nm-applet –sm-disable &

I did that, now my network manager icon disappeared from the top of the screen.  How do I get my connections back and visible..any help appreciated!

---

