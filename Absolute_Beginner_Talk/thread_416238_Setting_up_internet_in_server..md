---
title: "Setting up internet in server."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Rictus on 2007-04-20
Hi I'm trying to set up a MythTv box and I can't seem to find how to set up an internet connection.
Whenever I type in: cat /etc/network/interfaces 
I get: 
# The loopback network interface 
auto lo
iface lo inet loopback

iface dsl-provider inet ppp
provider dsl-provider


If I type in: sudo gedit /etc/network/interfaces
I get: 
sudo: gedit: command not found

Can someone point me in the right direction.
Thanks,
Rick

---

### Post by jtraub on 2007-04-20
Are  you running with Kubuntu?

---

### Post by jtraub on 2007-04-20
Oh.. It is server... 
You should use some console editor like vim.

try 
sudo vim /etc/network/interfaces
if it is not working you should perform
sudo aptitude install vim

---

### Post by Rictus on 2007-04-21
Awesome, actually I used nano. But without the suggestion of the editor I didn't realize how to access it. 
Ya, I'm your worst nightmare, a noob with a server.
Thank you.
Rick

---

