---
title: "Just installed NOW the network"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by happyhacker on 2007-01-09
I have just installed Ubuntu 6.6 on my network (PCW mag cd version). OK so far.

Eth port is recognised and I can open my netgear router (192.168.0.1) and see the management screen. I do not think it sees ubuntu yet.

If I go to my XP Pro laptop I cannot see Ubuntu on the network. The ubuntu machine is called 'sarah'. Configured for DHCP.

What do I do now?

---

### Post by Jussi Kukkonen on 2007-01-09
If you can connect to the router web interface from ubuntu, then the network is fine (the router definitely "sees you").

> If I go to my XP Pro laptop I cannot see Ubuntu on the network.
What does this mean? Did you try pinging (***ping ip-of-windows-machine*** in a terminal on ubuntu)?

---

### Post by sardion on 2007-01-09
If you mean you want the XP machine to "see" the ubuntu the way it sees other windows machines, you need to install the samba package (via synaptic).  This lets ubuntu do windows file sharing.  But unless you need that I wouldn't recommend it.  If you can http to the router, you should be able to get to the internet.

What else are you looking for?

---

### Post by louieb on 2007-01-09
I guess you want to set up file and printer sharing. But first I want to let you know about one handy feature of the net gear router that makes networking a little easier.   
Scroll down the left hand side and find * LAN IP Setup. Use this to give the Ubuntu box a static IP address. Instructions are on the right hand side. Even though the Ubuntu is using DHCP the router will give it the same IP address every time.

---

### Post by pross on 2007-01-09
I have a netgear, this function makes it sooo much easier for use with port-forwarding for torrents etc :)

It doesnt give your box a 'static' IP as such, the router still makes use of DHCP so ubuntu will get its IP thru DHCP, it just means your box will get the same IP every time so you can set port forward rules on the router.

---

### Post by happyhacker on 2007-01-09
Bit disappointed I've got to download SAMBA! How do I download it from my XP machine.

How do I find out the MAC address of the UBUNTU PC as I want to check the router is pointing to the right IP?

The I've got to connect it all to the BT Home Hub I've got.

---

### Post by louieb on 2007-01-10
Uh is the Ubuntu box hooked to the router or to a hub? If its connected to a hub then I don't believe that will work. It needs to be direct connected to the router. 
To get the MAC address its
Applications>Accessories>Terminal>ifconfig
Look for HWaddr. Here is what one looks like. (yours will be different)
 HWaddr 00:11:2F:D5:4E:0A

---

