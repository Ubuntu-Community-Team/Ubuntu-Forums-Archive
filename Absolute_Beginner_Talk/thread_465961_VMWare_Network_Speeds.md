---
title: "VMWare Network Speeds"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by tompickles on 2007-06-06
I installed Ubuntu in a Virtual Machine using VMWare Server on my XP box, which is connected to the internet (1 Meg connection) behind a ASDL router - safest way!

However, my download speeds in the virtual machine are really really really slow. My firewall in XP as been told to allow all VMWare programms as they've popped up.

Any ideas?!

EDIT: I can actually connect to the internet through the virtual machine, so a connection is there.

---

### Post by jverkamp on 2007-06-06
Check the network usage on the host machine (use Task Manager), how much bandwidth is being used?  Basically, is the VM actually getting to the network or is something on the local machine stopping it?  If it is getting through, are the responses going to the host and not the VM possibly...

Also, which option did you choose for the network? Bridged, NAT, local-only, etc...

---

### Post by tompickles on 2007-06-06
Bridged. And the connection to my Local Area Connection is about 0.36%

Both VMnet 1 and 8 are 0% yet the internet works withing the machine.

---

### Post by Anicka on 2007-06-06
> **tompickles said:**
> Bridged. And the connection to my Local Area Connection is about 0.36%

Both VMnet 1 and 8 are 0% yet the internet works withing the machine.

For me bridged doesn't work, only NAT. Play with the options and see what happens.

---

### Post by Dedoimedo on 2007-06-06
Hello,

Among many other things, I'm running various Windowses and Linuxes as virtual machines both in Windows and several Linux distros, all NAT. In Windows, I have noticed that the connections are a bit slow at the beginning but sort themselves out after a few seconds. Throughput works at full speed (download).

It might have to do with your firewall (SPI??)
It might have to do with your connection / overall load (P2P and such??)

I would suggest you try NAT and see how it goes. Also, do not forget to install VMware Tools.

Dedoimedo

---

### Post by tompickles on 2007-06-06
thanks. my firewall isn't blocking any VMWare software. And, i have no P2P open. I did have to use port forwarding on uTorrent to get teh speed abouve 10 kb/s on my XP box though, so, coud this be the issue?

---

### Post by Golyadkin on 2007-06-06
What are you downloading with? If you use bittorrent or aMule or something like it, you need to forward the ports on your router to the ip address of the virtual machine if you use NAT.

---

### Post by tompickles on 2007-06-06
downloading like updates from installers eg Debian, and direct from web server via links eg Gentoo

---

### Post by seanyseansean on 2007-06-07
I have this problem. It seems to be specific to some network cards.

My fix is to type:

sudo ethtool -K eth0 tx off
sudo /etc/init.d/vmware restart

Does this help?

---

### Post by tompickles on 2007-06-10
Sorry for delay - not yet tried this, but I will. Just a thought - how can i speed up the speeds before I actually have a loaded system - ie whilst installing?

---

### Post by spockrock on 2007-06-13
I tried this an I still have bad networking I am going to try nat and see if I can get it to work.

Ok the fix is easy for me, remove the vmware server, from the repos, then install vmware manually and everything works as it should

---

