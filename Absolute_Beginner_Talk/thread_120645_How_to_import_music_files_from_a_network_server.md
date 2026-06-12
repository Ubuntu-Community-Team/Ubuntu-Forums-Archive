---
title: "How to import music files from a network server"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by Netcab on 2006-01-23
Hi,
this is probably a stupid question but I'm loosing lot of time just for it...
I would like to create my music catalogue into applications like rhythmbox. 

I have a lot of music into my network file server (Windos XP, yet)  that I can access from Nautilus,  play my mp3 files, ecc.

The problem is that I cannot create a catalogue because rhythmbox cannot see the network, just local FS.

My file server has IP 192.168.0.2
My computer with Ubuntu is 192.168.0.10

Thanks for your help.

---

### Post by terrukallan on 2006-01-23
Installing the smbfs package will let you mount smb shares (Windows XP shared folders) as part of the local filesystem via the smbmount command.

---

### Post by doclivingston on 2006-01-24
Versions of Rhythmbox up to 0.9.2 don't support remote gnome-vfs mounts. The only way to access network files in those versions is to mount it properly, as terrukallan alluded to with the smbmount command.

Rhythmbox 0.9.3 (which should be released soon) has full support for remote gnome-vfs.

---

### Post by Netcab on 2006-01-24
Thanks for your reply. I'll try it.
Do you know another mediaplayer able to access network files natively ?

---

### Post by doclivingston on 2006-01-24
[QUOTE=Netcab]Do you know another mediaplayer able to access network files natively ?[/QUOTE]

Totem can (at least in Dapper, the version in Breezy probably does). Banshee, Muine, and Quod Libet can't. I'm not sure about anything else.

---

### Post by AndyCooll on 2006-01-24
Have you tried Amarok?

:cool:

---

### Post by Netcab on 2006-01-24
I have tried Amarok. Same problem

---

