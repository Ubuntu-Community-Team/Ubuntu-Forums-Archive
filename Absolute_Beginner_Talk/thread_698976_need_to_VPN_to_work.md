---
title: "need to VPN to work"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by tango_ninja on 2008-02-16
I'm a n00b to linux and ubuntu. So far I'm enjoying the system, but I need to be able to connect to my desktop @ my workplace.

I've tried the RDP client that comes with Ubuntu and it's works great. What I need to do to connect to my desktop@work is VPN, and then RDP.

I've looked over the Ubuntu VPN guide ([https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)) but can't seem to get it working.

After installing **network-manager-pptp** I can't seem to run it. I don't know where it's been installed to. I found it under Applications > Internet (it was hidden, had to enable it through the menu mgr.) but when I try to run it, it throws an error:

```
Failed to execute child process "nm-vpn-properties" (No such file or directory)
```

help ?

---

### Post by farruinn on 2008-02-17
Based on the Wiki, you don't explicitly run the package you installed. It's a sort of add-on that extends the functionality of the network-manager applet, so you click on the network manager icon and go to 'add vpn connection'.

Also, are you certain your workplace uses pptp?

---

### Post by tango_ninja on 2008-02-18
thanks farruin. i have it up and working now :)

---

### Post by tango_ninja on 2008-02-18
looks like I spoke too quickly...

I have been able to add a new VPN connection to my Network Manager displayed in the top panel. whenever I try to connect to the connection not only am I not able to connect by VPN, but my Network Manager icon disappears altogether !! 

I am still able to browse the net (and am still connected locally) but am NOT connected to the VPN. any ideas? 

- why does the icon disappear, and 
- can I restart it somehow?

---

### Post by tango_ninja on 2008-02-19
OK, if anyone is reading this thread.... :)

I have my VPN pptp connection up and working. network manager doesn't disappear anymore, all is good.

1 last problem... when connected to VPN, I can only browse my workplace network, I can't just browse the internet like normal (i.e. i had to disconnect my VPN to connect to ubuntuforums.org and creat this post)

anyone know why this is happening, or what configuration I need to correct this?

I want to be able to browse the net and at the same time be VPNd to work

---

### Post by farruinn on 2008-02-19
I unfortunately don't have an ubuntu system on hand (it's on order from System76 though!) so I can't do any testing to help. This problem sounds like it might be a firewall issue at your workplace. Are you pulling an IP address via DHCP through the VPN? You might check if you are and what it is. If you're not on the proper subnet your workplace might not allow outbound traffic. It sounds like the VPN is working, so maybe an admin from your work can help too?

Sorry I don't have anything more concrete.

---

