---
title: "Opening ports"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by scratched on 2006-04-16
I need to open port 3306 for localhost to connect to localhost to get my MySQL server to work, but I'm new to linux and don't know what I'm doing.

What do I need to do to open the port?

I've searched the forums for how to open ports and found this guide for opening the ports on iptables [http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661), but that guide doesn't help me since I don't really know how to do everything in linux yet.

---

### Post by frodon on 2006-04-16
If you didn't install any firewall programs or scripts on your computer your port is already opened because all the ports are opened by default.
If you're really new to linux and wish to set a firewall with a GUI i advice you firestarter which is a front end for iptables, use this commqnd in a terminal to install it  : ```
sudo apt-get install firestarter
```
But again if you didn't install anything the port is opened.

---

### Post by scratched on 2006-04-16
I didn't have firestarter on my computer, but for some reason the port was closed anyway. I'm not sure why.

I had firestarter but I couldn't figure out how to add policies. It turns out that I just wasn't thinking hard enough. I figured out how to use firestarter now...

---

### Post by Seaman on 2006-04-16
[QUOTE=frodon]If you didn't install any firewall programs or scripts on your computer your port is already opened because all the ports are opened by default.
If you're really new to linux and wish to set a firewall with a GUI i advice you firestarter which is a front end for iptables, use this commqnd in a terminal to install it  : ```
sudo apt-get install firestarter
```
But again if you didn't install anything the port is opened.[/QUOTE]
Isn't iptables installed by deafult?

---

### Post by frodon on 2006-04-16
Yes of course, but the policies are set to accept all by default after an ubuntu installation, that is why if you didn't change anything with your iptables configuration all your ports are opened.

---

