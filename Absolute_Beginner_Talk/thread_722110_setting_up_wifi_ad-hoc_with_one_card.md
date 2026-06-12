---
title: "setting up wifi ad-hoc with one card"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by drunkmatador on 2008-03-12
I'm on a network where I can only have a limited number of MAC addresses configured to work with the wifi. It's at an apartment building so I share this connection with 20-30 other people.

Since I can't have my laptop set up to connect to the network, I'd like to configure it to connect to my desktop computer, which is connected to the wireless connection. It seems like this would be possible but I don't have any idea how it would be done. Any suggestions?

---

### Post by handydan918 on 2008-03-12
Yeah, how about using the same mac as your desktop is using? That way you don't need to try to connect to the desktop. Just connect to the router...

[Here's how.]("http://wiki.archlinux.org/index.php/MAC_Address_Spoofing")

---

### Post by drunkmatador on 2008-03-12
sudo: /etc/rc.d/network: command not found

and

bash: /etc/rc.d/network: No such file or directory

and

bash: /etc/rc.d: No such file or directory

are all the errors i'm seeming to get. missing packages? i've got the most recent download of ubuntu but no updates on that computer, since i haven't gotten the internet to work yet.

---

### Post by handydan918 on 2008-03-13
OK, in place of the /etc commands, use ifdown eth? and ifup eth? where ?= designation of interface to be changed on your machine.

---

