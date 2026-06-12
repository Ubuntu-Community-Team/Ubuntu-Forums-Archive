---
title: "How do I set up VPN?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Krystoll Meth on 2007-03-22
Ok, I can VPN to other computers from my office computer (WinXP Pro system), and am running Ubuntu Edgy Eft at home, and have a wireless Belkin router (although I'll be getting a new one soon...damn piece of crap).  How exactly would I go about setting up my home computer so that I can VPN to it from my office computer?  Any help is much appreciated, especially on my first post :-)

---

### Post by cowlip on 2007-03-22
Welcome to UF :)

THere are some links in the Ubuntu Wiki which you might like until someone more knowledgable helps you here: [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=vpn&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=vpn&titlesearch=Titles)

---

### Post by Krystoll Meth on 2007-03-22
Aye, haven't looked yet but from all I've seen here, I'm fairly sure it'll be helpful :-)  Thank you!  All other help still appreciated, best community I've ever signed up for I think.

---

### Post by Krystoll Meth on 2007-03-23
Bump....

---

### Post by macogw on 2007-03-23
sudo apt-get install vpnc

To run it:
sudo vpnc

It'll ask for the gateway address.  Enter it (when I use it, I put 10.10.254.254)
hostname: (for mine, gwvpn)
group password: probably hashed on your thing, but decode it with [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode) 
then your username & password

To get the info, you can take the Windows vpn client .exe file and put it on Linux, then run "unzip vpnclient.exe" or whatever it is.  The .pcf file has all the info inside it.

Alternatively, 
sudo apt-get install vpnc kvpnc

You can import the .pcf file into kvpnc (but yeah, you still have to unzip it)

Also, in Feisty, there's a network-manager-vpn which is a plugin for network-manager-gnome if you use that and it handles your vpn without you having type the info in.  both this and kvpnc can save the info in a keyring

---

### Post by cowlip on 2007-03-23
That looks like really good advice maco, I've copied and pasted for myself for later :)

---

### Post by Metacarpal on 2007-04-08
In case you're still watching this thread, or if anyone searches it later:

The easiest way to get connected to a Cisco VPN is to install the following packages:

vpnc
network-manager
network-manager-vpnc

Once those are installed (you probably already have network-manager, depending on what version of Ubuntu you're running), all you have to do is left-click the NM applet in your task bar, and you'll find a VPN menu in which you can import the .pcf config file.

---

### Post by Jeff Johnston on 2007-04-21
Thank you! These directions worked perfectly. I was unable to use the cisco vpn and now I am glad it was broke because this is way more slick :).

---

