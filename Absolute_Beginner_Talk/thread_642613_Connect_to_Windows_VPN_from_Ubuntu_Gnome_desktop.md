---
title: "Connect to Windows VPN from Ubuntu Gnome desktop"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by UbuntNic on 2007-12-16
It's my second day with Linux and Ubuntu -- I'm starting to feel like an old hand. Or maybe just ... *old.* But things are going well. I have LAMP configured on Ubuntu 7.10 Server (Gutsy Gibbon?) and I installed the Gnome GUI so I'd at least have a clue. Now I'm trying to connect to my Windows Server 2003 PPTP VPN at work.

I found a post that suggested I do this: "sudo apt-get install network-manager-gnome network-manager-pptp", then go to Network Manager, select "VPN Connections" and configure the VPN connection.

So ... I did that.

Sure enough, I found "Network Manager" up there in my Notification Area. When I click on it my only option is "Manual Configuration..." That brings me to the Network Connections applet with four tabs: Connections, General, DNS and Hosts. Nothing about VPNs or PPTP connections.

Where am I going wrong? Whatever help can be offered by the group will be greatly appreciated.

UbuntNic

---

### Post by cmnorton on 2007-12-19
The only way I know to make this work is through Network Manager, when the network devices are all in roaming mode -- that is you are getting your IP address from DHCP. 

I would back up /etc/network/interfaces like this 

sudo cp /etc/network/interfaces /etc/network/interfaces.manconfig

Then, I'd edit /etc/network/interfaces, so it has these lines only:

auto lo
iface lo inet loopback

(sudo vi /etc/network/interfaces or use your editor of choice.)

Restart networking:

sudo /etc/init.d/networking restart

The last problem I had was probably due to the age of my Acer 630 Travelmate's built-in wireless card. I had to use a cardbus wireless card while working over a wireless network. Else, with a wired netword, everything worked fine, as far as setting up a VPN connection.

There are various posts in this forum, and a good one under tutorials that go into tweaking the VPN settings so you can get this working.

---

### Post by mentatxx on 2007-12-27
> **UbuntNic said:**
> 
I found a post that suggested I do this: "sudo apt-get install network-manager-gnome network-manager-pptp", then go to Network Manager, select "VPN Connections" and configure the VPN connection.

So ... I did that.

Sure enough, I found "Network Manager" up there in my Notification Area. When I click on it my only option is "Manual Configuration..." That brings me to the Network Connections applet with four tabs: Connections, General, DNS and Hosts. Nothing about VPNs or PPTP connections.

Where am I going wrong? Whatever help can be offered by the group will be greatly appreciated.


I  have got same error. :confused:
network-manager-pptp have been installed, but VPN option doesn't appear :-(

---

### Post by zero-9376 on 2007-12-27
maybe logging out or restarting, I don't recall having to do this myself but it is possible and i have the vpn connections option on both my desktop and laptop

---

### Post by UbuntNic on 2007-12-27
> **zero-9376 said:**
> maybe logging out or restarting

Thanks for the suggestion, Zero. I did try that, but to no avail. Still hoping someone from this forum can point me in the right direction.

---

### Post by The Cog on 2007-12-27
The debian howto says to install ppptpconfig, but that is not in the Ubuntu repositories. However, there is a package called network-manager-pptp which could be worth trying.

Alternatively, I have succesfully followed the configuration by hand instructions from the howto, and I confirm that they work on everything from Dapper to Gutsy.
[http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml)

---

### Post by ario on 2008-03-31
Hi
I've just reached to vpn connections window in my Ubuntu 7.10 by removing all lines in "/etc/network/interfaces" except those two lines that starts with "auto" and "iface". But when i try to add a VPN connection I will see a couple of settings and I have no answer to them. All I have is a simple windows xp vpn connection that i have configured it simply by all default settings and an IP address and user name and password. How can i configure my vpn connection in Ubuntu to work right when I know that this connection is works properly in windows xp and with its default settings. 
Thanks for you attentions.

---

### Post by ryanhaigh on 2008-03-31
The attached images show how I have my vpn connection set up. I too used the defaults under xp so these may help.

---

