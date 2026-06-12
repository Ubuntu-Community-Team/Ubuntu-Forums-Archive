---
title: "Shared Folder Doesn't Show Up in &quot;Network&quot; under &quot;Places&quot;"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by LordKelvan on 2008-02-12
Hi:

I have a weird problem.  I have a small home network, with two PC's, both running Ubuntu 7.10, each connected to a router via a wired connection.  I have a folder on PC #2, called Shared, which I am of course sharing, using NFS.  I can manually mount it on PC #1 using the command:

```

sudo mount ip_address_of_pc_2:/path/to/shared/folder /path/to/some/folder/on/pc/1

```

However, I cannot get the shared folder to appear in "Networks" under "Places" on PC #1.  The two computers are able to ping each other, and I can share a printer that is attached to PC #2.  I have tried turning off an IP filtering program I had running on PC #1, but that doesn't help either (PC #2 has no such software running).  PC #1 has nfs-common and portmap installed, and PC #2 has nfs-kernel-server, nfs-common and portmap installed.  The "Shared" folder on PC #2 has all permissions set (i.e. 777), so that anyone can create/delete files.

This is a bit of a convenience thing, but I would appreciate If anyone could help me out.  Given that I can mount the shared folder, I am sure its something stupid that I overlooked.

Thanks,
LK

---

### Post by oedha on 2008-02-12
have you install smbfs ? ( if you want to mount )
or you can also go to places - connect to server

---

### Post by LordKelvan on 2008-02-12
1) I am able to mount properly (and I am using NFS in any case).  

2) I tried using "Connect to Server" and selected "Custom Location" (is this the correct option to connect to a PC on the LAN?).  Under the URI I typed in the IP address of PC #2, lets say it was 192.168.1.30, and hit Connect.  I now get an entry called "192.168.1.30 on (null)".  However, when I double-click on it, it says "Couldn't find /192.168.1.30".  Could the "/" symbol in front of the IP address in the error message have anything to do with it?  Maybe I am specifying the URI incorrectly?

Thanks, keep the suggestions coming :)

---

### Post by oedha on 2008-02-12
did you choose the service type ?
or how bout this.....do on each unit ( since they are gutsy right ? )
to shared my laptop linux folder.....
go to system - administration - shared folder
click add button
choose teh folder that i'd like to share
pay attention on read only box

then....open terminal
type :==> sudo smbpasswd -L -a username ( make a username and password )

---

### Post by LordKelvan on 2008-02-12
Umm, perhaps I'm not being clear, but I am using NFS, not Samba, so I don't think creating a Samba password and username is going to work.

---

### Post by oedha on 2008-02-12
oo.....sorry......:)

---

### Post by LordKelvan on 2008-02-12
Its cool, anyone else have ideas on how to fix this ?

---

### Post by LordKelvan on 2008-02-16
Bump

---

### Post by LordKelvan on 2008-02-25
bump

---

### Post by Zill on 2008-02-25
FWIW I also use NFS but have never seen these servers or mounts under Places, Network.
It seems like this GUI only works if you use SMB networking - unless a guru can advise otherwise ;-)

---

