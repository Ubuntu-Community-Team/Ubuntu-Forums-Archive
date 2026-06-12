---
title: "Mapping Ubuntu hosted NTFS drive to Windows Vista"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by webwolf_3000 on 2008-02-03
Hi guys, new here

Basically what I want to do is run my Nix box as a complete web server.

So far, I think I have the network up and running, that is to say I can ping my Vista box from nix and vice versa.

Can't ping the netbios names, and cannot figure out how to map the nix NTFS drive to vista. any help would preciated.

Ive played around with the SAMBA as much as I can, but Cannot connect to the share, Im thinking it could be that I've set up the smb.conf up wrong.

the drive I want to share is:

Mount: /media/hda5
FS: fuseblk
Mount Opt: rwnosuid nodev noatime user_id=0
                   group_id=0 default_permissions allow_other

This was mounted by default at install of ubuntu, its basically the webserver left behind by xp when I wiped that to install Ubuntu.

the SMB file I'm using is the default smb.conf with the following appended:

[server]
comment = shared files
path = /media/hda5
writable = yes
browseable = yes
guest ok = no
printable = no

The domain name is set up as 'lair' - this worked ok for vista / xp mappings, so the domain basically works, the Vista machine is l'phoenix' and the nix machine is 'dragon'

so to map the drive, I should be inputting:
//dragon/server
The error I get is Network path not found

Thats pretty much everything I know.

---

### Post by hyperair on 2008-02-03
If your "dragon" has a fixed IP address, I'd actually just go with using the IP address, because XP and Vista's detection of other computers in the network is rather dodgy. Sometimes it works, sometimes it doesn't. When it works it's well and good, but when it doesn't, you gotta use the IP address instead. Like: \\192.168.1.2\server

At least that's what I use when I access my printer.

EDIT: However, you did mention you were running on a domain as opposed to a workspace, so you have some active directory service going on? If that was the case you shouldn't have a problem resolving the hostname of the other computer.

---

