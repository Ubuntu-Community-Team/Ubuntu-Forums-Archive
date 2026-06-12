---
title: "Ethernet Connection Sharing"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by Jivicin on 2005-08-04
I'm in the process of migrating from XP to Ubuntu, and thus far it has been easy thanks to the starter guide and these forums.

I ran into several small problems (i.e. Java plugin in Mozilla, integrated sound not working for my A7N8X mobo [nForce], etc.), but my most recent problem I haven't been able to work out yet.

My mobo has two embedded ethernet ports and I am attempting to bridge an internet connection between them.

In XP this was semi-simple, I would just select both connections from my network connections menu and bridge them, reboot the computer I'm trying to grant access to and I was done.

After hours of RTFMing, I've still had no luck.  I tried using firestarter to share the connection.  Nope.  I tried editing the settings under the network menu.  I've got eth1 going to my router and it's configured as DHCP.  eth0 is going to the other computer and I tried setting it up with at static IP of 192.168.0.3 (which was reserved on my router for that computer), and a subnetmask of 255.255.255.0.  That didn't work.  When I put in a default gateway of 192.168.0.1, neither connection would work.

On a completelty unrelated subject, I was wondering if someone could explain why in csh if I compile a C++ program why I can just type a.out and it will run as opposed to ./a.out.  What is the significance of the "./"?

---

### Post by az on 2005-08-04
If one NIC is getting the address 192.168.0.3 by DHCP and you are trying to assign it to the other nic, you will get a problem.

One nic should be on the 192.168.0.x network and you should make another a different network (like 192.168.1.x) with your ubuntu box routing the two together.

It should not be too hard to do with firestarter.

You can also set up a dhcp server so that you do not have to set a static address to your nic which will be connected to your other computer.


The ./ means to look in the current directory.  The current directory is usually not part of your path.

For your sound card:
[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

As well, there are precompiled java installers available which include a mozilla plugin.

---

### Post by Jivicin on 2005-08-04
The computer that is sharing the connection recieves 192.168.0.2 from the router.  

Before when I was running XP, the router would assign random 192.168.0.X IP's to the other computer, so I set it so the router recognizes the mac address of the second computer and always assigns it 192.168.0.3.

When I first configured firestarter, I went into the network settings menu and set both eth0 and eth1 to DHCP, and selected eth1 as my default gateway.

Firestarter did nothing when I tried to share the connection.

My other problems (sounds and Java) I worked out already, the connection sharing is the only thing I haven't been able to work out.

---

