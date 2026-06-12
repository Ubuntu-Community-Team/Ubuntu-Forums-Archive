---
title: "TightVNC woes!"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Copps on 2006-09-03
Hope someone can help.

I'm trying to set up remote desktop access to my Ubuntu machine, both from the other (Windows) machine on the same local network, and from my PC at work (external network).

I've set up port forwarding on my router for port 5900 to the internal IP of my computer, and followed the instructions at [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_configure_remote_desktop_.28not_secure.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_configure_remote_desktop_.28not_secure.29) for configuring remote desktop options.

I've downloaded TightVNC viewer to both Windows boxes, but when I try to run it to connect to Ubuntu by IP address, I receive a "Failed to connect to server" error message.

I expected to see something useful, somehere, in /var/log on the Ubuntu box, but there is nothing to help me. I don't run a firewall on Ubuntu yet. I've tried disabling the firewalls on the PCs I'm connecting from, to no avail. If I boot the Ubuntu box into it's Windows partition, I can connect Windows to Windows via RDP, so there's no issue with the machines I am trying to connect from recognising the IP address of the target machine.

Anyone have any other pointers please?

---

