---
title: "Bigpond (Australian) cable modem setup"
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by Halbert on 2005-11-03
Hi,
I need to get ubuntu to talk to my ISP via firefox!
I use Bigpond (Australian) cable. Their client does not work with Linux (expletive deleted) but there is on which does (bpalogin) I tried to install it but do not realy have a clue what I am doing.....
I managed to get the exe on the desktop but no luck with run or install.
Would someine please point me at the instructions for:
How does one install an application?
How to configure client?

---

### Post by mlomker on 2005-11-03
I'm not familiar Big Pond's cable modem setup.  Is it just an ethernet cable connection or some kind of USB adapter?  Does it just give you a DHCP address or do you have to use PPOE to connect?

---

### Post by matthewv on 2005-11-03
I'm not familiar with the setup either, but being Australian I have heard about it, and i think its basically that bigpond supplies a login client for your computer. This client sends the bigpond server a "heartbeat" to keep the connection alive, bpalogin is supposed to do something like that too.

---

### Post by Shauntp on 2006-11-18
Did you install it through synaptic package manager?

---

### Post by adam.tropics on 2006-11-18
It's in synaptic yes, and it's website is [here.]("http://bpalogin.sourceforge.net/index.php?page=index")

---

### Post by TheGrinch on 2006-11-18
From what I have read, the Bigpond heartbeat client is no longer required. Refer to [http://whirlpool.net.au/article.cfm/1662?show=replies](http://whirlpool.net.au/article.cfm/1662?show=replies)

I never needed it, but my cable modem is only about 18 months old & had a built in client.

What type of cable modem do you have? I have a Motorola SBG900 wireless cable modem & have it set to assign IP addresses to clients via DHCP. 

If using DHCP - On your Ubuntu PC open "Network Tools" > select the Network device e.g. "Ethernet interface (eth0)" > then click "Configure". Make sure your "Connection Settings" are set to DHCP and the "Enable this connection" checkbox has been ticked.

Now open "Network Proxy" > click on the "Proxy Configuration" tab & make sure "Direct Internet Connection" is selected.

I hope this helps.

---

### Post by adam.tropics on 2006-11-18
Yeah, how stupid am I!!! I use bigpond, and no, I don't use it either! The only thing I do use is a small [firefox extension]("http://netusage.mozdev.org/") to see my usage. D'oh!

---

