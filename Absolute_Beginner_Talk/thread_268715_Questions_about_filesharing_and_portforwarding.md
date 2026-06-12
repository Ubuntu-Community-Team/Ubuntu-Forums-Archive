---
title: "Questions about filesharing and portforwarding"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Beamvr6 on 2006-09-30
Hi,

I'm trying to set up filesharing with another computer in my local network and forward a port to my router for Azureus to get NAT OK. I've been searching the forums but couldn't find something relevant (maybe I didn't use the right search criteria).

Networking HW is an ADSL router with DHCP where it is possible to forward ports. Attached to this is a switch (not configurable). 
On the Ubuntu system there is a FAT32 partition intended to be used for sharing (or part of it).
The other computer is running XP and configured the XP way of sharing files.
Azureus is installed and can download / upload.

My questions are:
- Where do I have to go in Ububtu and what do I have to do to enable filesharing with the XP system?
- Where do I have to go in Ububtu and what do I have to do to forward a port (say 12345) for Azureus?

TIA

---

### Post by easyease on 2006-09-30
can you access your router through a browser? what make of router is it?

---

### Post by jd65pl on 2006-09-30
You should probably have a look at samba for file sharing with windows. Have a look at the page below
[URL="https://help.ubuntu.com/community/SettingUpSamba"]
https://help.ubuntu.com/community/SettingUpSamba[/URL]

Thanks

J

---

### Post by jorn on 2006-09-30
To share files with xp you can use Samba. I don't have link for you, but it is in Synaptic the Packetmanager. Samba+smbfs I think. Try a search.

You must do your portforwarding in your router:
[http://www.portforward.com/](http://www.portforward.com/)

---

