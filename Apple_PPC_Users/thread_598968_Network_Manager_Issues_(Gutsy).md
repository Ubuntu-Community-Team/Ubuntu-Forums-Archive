---
title: "Network Manager Issues (Gutsy)"
date: 2007-10-31
forum: Apple PPC Users
---

### Post by MacBookJoe on 2007-10-31
[B]My 'System Monitor' reads the 'Network Manager' Process at >90% 

My CPU load is running at 100% all the time now. If i end the NM process the load drops back to 12-40% with a couple apps running.

Anyone else had this problem or know a solution?


I re-installed the NetworkManager from the Ubuntu Install CD and still no improvement.


Any help would be great.[/B]

---

### Post by ssam on 2007-11-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155572](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155572) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155572](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155572)

not sure of a workaround or solution yet. i might have another go at the weekend

---

### Post by pxwpxw on 2007-11-02
> **ssam said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155572](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155572) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155572](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155572)

not sure of a workaround or solution yet. i might have another go at the weekend

One workaround is to remove packages <network-manager> and <network-manager-gnome>, then just use the network-admin basic network config (System:Admin:Network), or install wicd. Stops the 90% cpu load. Only had the problem with ubuntu desktop, xubuntu had no problem, both using dist-upgrade to gutsy.

---

### Post by MacBookJoe on 2007-11-06
Cheers guys.


I ended the Process as a quick workaround and then 'Software Updater' updated it yesterday, Issue gone.

---

### Post by Doctor J on 2007-11-06
> **ssam said:**
> 
				[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155572](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155572)

not sure of a workaround or solution yet. i might have another go at the weekend

Don't take this as a personal attack, but i'm curious how this got released onto the installer disk image without anybody noticing.  

I have a similar but worse problem - Network Manager is running at 96.2 % CPU *and* refuses to acknowledge the presence of the ethernet cable.  Killing the network manager process at least allows me to use the system with a certain degree of responsiveness, but still doesn't allow to connect to the network.  I uninstalled the Network manager, then tried reinstalling it: no dice, because no connection.  So i'm left with a system that can never be updated, only re-installed.  What are the odds a patched Gutsy install disk can be put together before i find where i put my Feisty disk?

As a final comment, i see the "Networking and Wireless" forum is currently racking up ~ 20 requests for assistance per hour, and most of them are going un-replied.

---

### Post by ssam on 2007-11-07
> **Doctor J said:**
> Don't take this as a personal attack, but i'm curious how this got released onto the installer disk image without anybody noticing.  


its hard to test when the live cds don't boot :-(

> **Doctor J said:**
> 
I have a similar but worse problem - Network Manager is running at 96.2 % CPU *and* refuses to acknowledge the presence of the ethernet cable.  Killing the network manager process at least allows me to use the system with a certain degree of responsiveness, but still doesn't allow to connect to the network.  I uninstalled the Network manager, then tried reinstalling it: no dice, because no connection.  So i'm left with a system that can never be updated, only re-installed.  What are the odds a patched Gutsy install disk can be put together before i find where i put my Feisty disk?

As a final comment, i see the "Networking and Wireless" forum is currently racking up ~ 20 requests for assistance per hour, and most of them are going un-replied.

you should be able to use the old System->Administration->Network tools to set up the network. untick the roaming box.

---

### Post by js1 on 2008-03-25
Just helped a coworker install Kubuntu Gutsy on an iBook G4.  We're seeing similar behavior from NetworkManager.  Tailing the syslog, we're seeing the following non-stop:

> Mar 25 18:20:41 my-ibook NetworkManager: <info>  Activation (eth0) New wireless user key for network 'MyWirelessNetwork' received.
Mar 25 18:20:41 my-ibook NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 25 18:20:41 my-ibook NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 25 18:20:41 my-ibook NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 25 18:20:41 my-ibook NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 25 18:20:41 my-ibook NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 25 18:20:41 my-ibook NetworkManager: <info>  Activation (eth0/wireless): access point 'MyWirelessNetwork' is encrypted, but NO valid key exists.  New key needed.
Mar 25 18:20:41 my-ibook NetworkManager: <info>  Activation (eth0) New wireless user key requested for network 'MyWirelessNetwork'.
Mar 25 18:20:41 my-ibook NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.


The problem is NetworkManager isn't prompting for authentication info for MyWirelessNetwork.  The  x86 and amd64 versions pop up the KNetworkManager dialog for the authentication info.  Any ideas why NetworkManager on the powerpc port isn't prompting for the authentication info?  Thanks for any insights.

---

### Post by stream303 on 2008-03-25
> **Doctor J said:**
> Don't take this as a personal attack, but i'm curious how this got released onto the installer disk image without anybody noticing.

That's how I felt when it happened to my G4 iBook.  On my G5, NM is no problem.  It is also a problem on Debian on my G5 under certain circumstances, so don't sweat it. :)

I think the cleanest solution is to disable it, and not uninstall it, as described here:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

Since I'm not running wifi, and don't need to roam, NM is off of my G4 and G5 by disabling them.  I did have to reboot and go back and reestablish my network settings.  So far so good!

See if disabling, rather than removing might help.  Even if it gets upgraded, it is disabled, so no problems there...

---

