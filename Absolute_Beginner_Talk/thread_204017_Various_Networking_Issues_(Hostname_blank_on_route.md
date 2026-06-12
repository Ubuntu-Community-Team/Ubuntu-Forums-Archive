---
title: "Various Networking Issues (Hostname blank on router, DHCP, Static IP, Samba dropouts)"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Crucinator on 2006-06-26
Hello.  I'm new to Linux and Ubuntu, and have spent the last couple of weeks reading a lot of useful information on this forum and the Ubuntu wiki, but I still have some networking issues that I have not yet resolved.  I'm sorry if grouping all of my bugs into one post is bad forum etiquette, but they may all be related so that is why I did it.

I am using a P3 Dell GX300, 384 RAM, and an 80GB HD.  I am connecting via my wireless card (Linksys PCI WMP54G v1.2) to a Linksys WRT54G v1.1 with latest firmware.  I followed the guide to add bcm43xx drivers, and also installed NetworkManager.  I usually have no problem connecting to the network when the router's DHCP server is enabled, and the configuration of the wireless card is also set to DHCP.

The first problem I have is the hostname for this Ubuntu box is blank in the DHCP client list of the router.  I have set a hostname via the networking administration panel in Ubuntu, but it doesn't show up on the router's web configuration screen.

The second problem is how I want this Ubuntu box to connect to the network.  I want to run it as a webserver, and have it connect with a static IP address.  Whenever I change the settings via the networking administration panel in Ubuntu to a static IP, the connection drops out.  I reviewed the etc/network/interfaces file, and it looks okay to me (a complete noob), but no luck.  So therefore I've only been able to connect via DHCP.

I only want to allow the DHCP server of the router to allocate 3 IP addresses to the local network (the Ubuntu box, one wireless XP laptop, and one wired XP desktop).  I want the XP laptop to be 192.168.1.101, XP desktop to be 192.168.1.102, and the Ubuntu box to be 192.168.1.103.  Say for a moment this works correctly.  If I decide to reboot the Ubuntu box, it will not reconnect to the router, even if I remove and refresh the lease as 192.168.1.103.  I have to add another IP address and the Ubuntu box connects as 192.168.1.104.  No matter what I do, I cannot force the Ubuntu box to connect as 192.168.1.103.  It makes port forwarding a hassle every time I perform upgrades.

Last but not least, occasionally I connect to my XP laptop via Samba to grab some files.  At first everything works fine, but it seems when the screensaver kicks in on the XP laptop the connection severs.  I try to reconnect, but the workgroup doesn't appear on the network servers menu.  I have to reboot and wait for what seems like 20 minutes for the workgroup to reappear.

To summarize:
1.  Hostname is blank in the router
2.  I cannot connect as a static IP at all
3.  The DHCP connection with NetworkManager and the router doesn't refresh connection leases and causes irritating address connection and port configuration maintenance
4.  The Samba/Windows connection drops out frequently

If you made it this far and can help, thank you so much!

---

### Post by ash211 on 2006-06-26
I think the answer to your first question is here: [http://ubuntuforums.org/showthread.php?t=55564](http://ubuntuforums.org/showthread.php?t=55564)

The relevant bit is this:
[QUOTE=Joeak]Try editing your /etc/dhcp3/dhclient.conf file and unremming/editing the line:

send host-name "yourhostnamehere";

Then do:

sudo /etc/init.d/networking restart
sudo ifup eth0[/QUOTE]

Edit /etc/dhcp3/dhclient.conf with this command:
```
gksudo gedit /etc/dhcp3/dhclient.conf
```

---

### Post by Crucinator on 2006-06-26
Thanks!  This worked great and my hostname now appears.

Can anyone help with my other issues?

---

### Post by ash211 on 2006-06-27
I'll give them a shot, now that the easy one is out of the way!

2) Could you post your /etc/network/interfaces file so we could take a look at it?  Static IP addresses should work just fine from there.

3) Will the XP boxes reconnect as their original IP, or is it just a problem with the Ubuntu box?  It sounds like what you're looking for is called 'static DHCP'.  From [www.dd-wrt.com]("http://www.dd-wrt.com/wiki/index.php?title=Static_DHCP"):
> How does static IP address assignment work?

Your computer boots and requests its IP from the router's DHCP server. The DHCP server recognizes the MAC address of your PC's network card and assigns the static IP address to it. 

4) Make sure samba is fully updated.  And the rest of Ubuntu while you're at it: ```
sudo apt-get update && sudo apt-get upgrade
```
Start with that and we'll work more from there.

---

### Post by Crucinator on 2006-06-27
Ok, here is my etc/network/interfaces face while configured with DHCP...

auto lo
iface lo inet loopback
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
auto eth1

and here it is configured with a static IP...

auto lo
iface lo inet loopback
iface eth1 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.XXX
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
auto eth1

I was able to stay connected to the network once with the static IP, when I already had a DHCP lease for the same IP address.  When I try to refresh the network connection I'll get a pop up asking for my WPA key.  When I enter it, NetworkManager will search for a minute, and then it will ask me for the WPA key again.  It will never actually connect to the network.

Maybe I'm configuring my router the wrong way.  If I want to set static IP addresses for all my computers, can I turn off the DHCP server on the router?  If DHCP has to be enabled, do the static IP addresses have to fall within the specified leasing IP range?  I can never seem to control how the router leases out IP addresses...

Also, when I try to disable and re-enable networking with NetworkManager, the hardware configuration for the wireless card goes completely blank in the &#8220;Network Tools&#8221; application.  Why does this happen?

---

### Post by Crucinator on 2006-06-27
I'm sorry ash211, I didn't see your advice about [www.dd-wrt.com](www.dd-wrt.com).  I'll try that out and let you know if it works...

---

