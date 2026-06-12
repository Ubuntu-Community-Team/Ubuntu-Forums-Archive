---
title: "VPN in Ubuntu 6.10"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by alexandre.englert on 2007-03-20
Hello! I just installed the Ubuntu 6.10 in my laptop and I can only access internet in my house through a VPN connection to my university network. Which program is most proper to use?  I saw there is the KVpnc but I cannot install it since I cannot connect to the internet with the laptop. Is it another way of getting it (downloading) and how to install it?

Thanks very much.

Alexandre

---

### Post by eljalill on 2007-03-20
You could check, whether there is a VPN client on the CD.
For that you enable the CD as a source for synaptic (and disable all other repositories, so that you won't get swamped with error messages), and then press the reload button. Now look for a VPN client with the search function.
If you have Ubuntu (gnome), kvpnc might not be the best option, since it requires the kde libraries. Maybe better use vpnc or openvpn.

---

### Post by Hortinstein on 2007-03-20
[http://lug.wsu.edu/node/641](http://lug.wsu.edu/node/641) 

This is how I do it for my university, yours shouldnt be too different, you can alwasy look for a LUG (linux user group) on campus, they are pretty good at stuff like that

---

### Post by alexandre.englert on 2007-03-25
Hi! Thanks for the help. I have now installed OpenVPN in my Ubuntu 6.10 (through the Synaptics Package Manager) but I don't know how to execute it. Do you know how should I run it?
And by the way, we don't have a linux user group here at my university (bad...).
Thanks very much,

Alexandre

---

