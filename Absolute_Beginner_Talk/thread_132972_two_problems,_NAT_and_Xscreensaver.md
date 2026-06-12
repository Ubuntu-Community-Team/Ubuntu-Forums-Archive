---
title: "two problems, NAT and Xscreensaver"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by janus zeal on 2006-02-19
i have ubuntu (5.10) installed on my desktop and i have two problems...
my old windows system was set up like a router/dhcp server (useing internet connection shareing) for my other pc and xbox, now that i have linux i dont know how to set something like this up...
DSL modem --- wifi router ))) windows pc --- ethernet switch --- XBOX / PC
*--- is eithernet, ))) is wireless*

my other problem is that when ever the xscreensaver starts (or i open screensaver prefs) the system freezes...

thank you very much to anyone who replys... ^_^

*im going to start over being a noob with linux...* >_< lol

[edit]the mouse doesnt freeze, but everything else does...idk if that helps any[/edit]

---

### Post by Pragmatist on 2006-03-11
I would try and build that chain one piece at a time, starting with having an internet connection using the wireless router.  Check these out for starters:
[https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifi%29](https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifi%29)
[https://wiki.ubuntu.com/WiFiWithSomeoneElsesRouterHowTo?highlight=%28router%29](https://wiki.ubuntu.com/WiFiWithSomeoneElsesRouterHowTo?highlight=%28router%29)

For xscreensaver try this:  
make a backup of your /etc/gdm/gdm.conf file:
```
sudo cp /etc/gdm/gdm.conf /etc/gdm/gdm.conf.bak
```
Now edit your gdm.conf file:
```
sudo gedit /etc/gdm/gdm.conf
```
Search through the file (your editor's search feature can be handy here) for lines containing the keywords: suspend  and  hibernate
comment these lines out by putting a # at the beginning of those lines, save the file, exit the editor and reboot (technically you don't have to reboot, you just need to restart/reload gdm; but do it this way for now. It is simpler.) 
Now try xscreensaver.

Good Luck! and let us know what happens.

---

