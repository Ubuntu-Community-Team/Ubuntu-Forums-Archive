---
title: "Windows 2000 Network: Integrating Linux"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-03-20
Hi,
I have a Windows 2000 Professional / WindowsXP based home network, peer-to-peer, where one computer (the Win2K box) acts as ICS and printer 'server'. I'm pretty sure the Win2K ICS thingie apparently does kind of a mini-dhcp service, since when it was just a Windows-only network (no Linux boxes), the 192.168.xxx.xxx octet would change for the 'clients' - those connected to the switch who *don't* have a direct connection to the internet - every time we booted up the Win2K box. I tried to set up my little network using static IP addresses but couldn't seem to get the 'client' boxes to see the ICS box, so I had to put it back to dhcp.

Now I've installed Ubuntu 6.10 on my laptop and desktop. From what I understand, NFS is the preferred protocol to connect the two together - however, my desktop doesn't have NFS enabled for some reason. I was wondering if there's a tutorial (simple, for n00bies like *me*) that would walk me through setting this all up... NFS and Samba. 

...or...

which files do I edit to 'enable' NFS?

BTW, I will eventually convert the Win2K box to Linux, but the same issues apply: no one else in the house as thrilled with the Ubuntu as I am - they're all running WIndows! - so the server will have to stay as it is until I get another box up and running Linux ICS / printer-sharing / firewall / and all that seamlessly.

Cheers,
Robyn

---

### Post by steve101101 on 2007-03-20
try these links for how to guides

[http://ubuntuforums.org/showthread.php?t=202605&highlight=setup+up+samba+peer-to-peer](http://ubuntuforums.org/showthread.php?t=202605&highlight=setup+up+samba+peer-to-peer)

[http://ubuntuforums.org/showthread.php?t=88206&highlight=netbios](http://ubuntuforums.org/showthread.php?t=88206&highlight=netbios)

---

### Post by steve101101 on 2007-03-20
I run this linux computer on a windows network, but the DHCP's are given out by the switch/router box. It runs great for me.

---

### Post by steve101101 on 2007-03-20
> **Robynsveil said:**
> 
BTW, I will eventually convert the Win2K box to Linux, but the same issues apply: no one else in the house as thrilled with the Ubuntu as I am - they're all running WIndows! - so the server will have to stay as it is until I get another box up and running Linux ICS / printer-sharing / firewall / and all that seamlessly.


im in the same boat with my family. i do printer sharing and file sharing

---

### Post by Robynsveil on 2007-03-20
Thanks for that, Steve. Quick question  - it's still not working as advertised, so do I ask that Stormbringer person my followup questions or can I ask them here? Anyway, I'll have a go here...

I followed the steps of the tutorial, installing and enabling Samba on my laptop. Then I booted up my desktop to WinXP... in the Workgroup (My Network Places) I can see my laptop and the shared drive, but I can't access it.

Now, in the smb.conf file, I've got the following entries:
[Content]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = robyn
    force group = robyn

In the [] brackets I put the actual name of the Ext3 folder I'm trying to share with Windows.
Any idea what I'm doing wrong?

Cheers,
Robyn

---

