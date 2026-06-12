---
title: "Firewall blocks when I try to see other computers in the workgroup"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Joakim Stokland on 2007-07-14
Hi! I've searched through this forum, and I can't find anything that helps me. If you know about a previous post, please point me to it.

I've been trying to set up a home network where my girlfriend and I can share files. She uses Windows, and I've got Ubuntu. Earlier I could access her files, but after I installed Firestarter and configured iptables, I can't. I get this message when I try double clicking Samba Shares:
"Unable to find any workgroups in your local network. This might be caused by an enabled firewall."
I have the standard setting with permissive outbound policy and restricted policy for inbound connections.
I have tried to allow Samba, and both her, mine and the router's IP's.
If I disable the firewall I'm able to see the workgroup and access her computer. How can I allow this with the firewall enabled?

Thanks!

Joakim

---

### Post by BobCFC on 2007-07-14
There should be a box to tick on firestarter to enable samba?  Any way [here]("http://troy.jdmz.net/samba/fw/") is a tutorial to do iptables manually for samba. 

You need to open 
137/udp 
138/udp 
139/tcp 
445/tcp

---

### Post by Joakim Stokland on 2007-07-14
Thanks!
Those are the ports I have already opened. I didn't find anything about Samba specific in the settings section. Could it be the "enable DHCP for the local network" or something?

And what is UDP and TCP?

---

### Post by xpod on 2007-07-14
When you click the "policy" tab in firestarter you then right click the "allow service ports for" window and then ADD RULE

You should get the below box pop up
[ATTACH]38153[/ATTACH]

EDIT:sambas further down the list and out of view in the screenshot
[http://www.fs-security.com/docs/policy-page.php](http://www.fs-security.com/docs/policy-page.php)

---

### Post by Joakim Stokland on 2007-07-14
That was what I did too. I simply selected SMB from the drop down menu. The ports BobCFC listed were automatically filled in.

I tried adding the port that showed up in the events list; 32824. When I was finished typing, "Sun-RPC portmap" showed up in the name box. Now I can access the files!
What is Sun-RPC portmap?

---

### Post by BobCFC on 2007-07-14
TCP and UDP are the protocols used by the internet on top of IP addresses.  TCP is for two-way conversations with normal traffic that must arrive in the correct order such as file sharing.  UDP is for broadcast stuff like watching streaming video where dropping the odd packet is less important than fast frame rates

---

### Post by Joakim Stokland on 2007-07-14
Okay, now I understand! :)
Thanks to all for your answers!
Joakim

---

