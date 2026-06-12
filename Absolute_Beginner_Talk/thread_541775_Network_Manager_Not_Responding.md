---
title: "Network Manager Not Responding"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Guruprasad on 2007-09-03
I had setup my network to access the internet. It was working fine.

Now I need to change the settings like ip address etc. Bu t when I open Network Manger and try to open properties of Network connection the system stops responding.

Is there any other way of changing the settings? Are these settings saved in any file which i can edit directly? Or any command from terminal which can change it?

---

### Post by southernman on 2007-09-03
A pretty good head start to using ifconfig on the command line is below...

[http://www.debianadmin.com/network-interface-configuration-using-ifconfig.html]("http://www.debianadmin.com/network-interface-configuration-using-ifconfig.html")

---

### Post by runemaste644 on 2007-09-03
Wow, your network manager is not responding!
Mine is just broken overall after a sudo dpkg-reconfigure
Maybe go on another computer and go to packages.ubuntu.com and download network-manager and (assuming you have Gnome as your WM) network-manager-gnome to a flash drive, re-install from there (remove the packages in Synaptic first) and that could fix it probably.

---

