---
title: "Question about network"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2008-01-06
Hi – I _dont_ have a problem, just a question. 

I wanted to find my IP, and since I know nothing about networking I had to look for some guides. I started to read the Ubuntu documentation and thought it was strange that all the info didn't match what I had for my Ubuntu regarding networking. 

My desktop pc have a wired network card(connected to a router), and it worked after the installation of Ubuntu. I do not have a wireless card at all.  When I go to System > Administrasjon > Network there is two «Connections», one «Wired Connection» and one «Modem Connection». Both had a minus in front of them. When I clicked on the Wired Connection and choose «Properties», the «Enable roaming mode» was checked, and all the others where greyed out. When I looked at the /etc/network/interfaces it stood only: 
[I]auto lo

iface lo inet loopback[/I]

I unmarked the «enable roaming mode» and choose «Automatic configuration(DHCP)(but nothing more). I dont have a static IP. I then lost the connection to Internet, but it was back after rebooting(I had to choose eth0 under the Connection Properties first from the Network applet on the panel). 

When I now go to /etc/network/interfaces it stand
[I]auto lo

iface lo inet loopback

iface eth0 inet dhcp

auto eth0[/I]

_My question is this:_
Why did it stand «Enable roaming mode», isn't this something for laptops and wireless networking? So why did it work (so well) on my wired connection. 
Is it possible to restart the connection – so you dont need to reboot?
How can I see the internal IP(for the house LAN), and how can I find the IP for my pc on Internett? I have looked at «ipconfig», but I didn't understand much. 

Thanks for any answers – and sorry if this is stupid or something like that.

---

### Post by p_quarles on 2008-01-06
To restart the network:
```
sudo /etc/init.d/networking restart
```
To get your PC's IP address:
```
ifconfig eth0
```
it's in the second line.

To get the public IP address, you'll need to query an external server, e.g. whatismyip.com. If you want a quick command line solution, there's this. Install "curl":
```
sudo apt-get install curl
```
And use the following command:
```
curl 'http://www.whatismyip.org'
```

---

### Post by esodin on 2008-01-06
From the desktop:

To see your IP: Right-click on the network icon (two computers) on your status bar and select "Connection information"

I believe roaming (for a wired connection) only means that it will get an IP-address from an DHCP server on your network.

To restart your network adapter right-click on your network icon and un-check  "Enable Networking" then  right-click on your network icon, again and check "Enable Networking"

---

### Post by _sAm_ on 2008-01-06
Big thanks to you both for your answers:-) 

The "Connection information" is greyed out, so I cant click on it. But I am connected.

---

