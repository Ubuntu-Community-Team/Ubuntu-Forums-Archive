---
title: "How to mount and NFS drive  ?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-04-24
The help says to

"To access network places, open the file manager and choose Places &#8594; Network Servers. A window opens that displays the network places that you
can access. Double-click on the network that you want to access. 

To
access UNIX shares, double-click on the Unix Network (NFS) 
object. A list of the UNIX shares available to you is displayed in the file
manager window."

Well, it doesn't work like that.  The Places menu, has a menu item called "Connect to Server" and that's the nearest thing, except maybe "Network"

"Connect to server" has Webdav, Windows share, ftp, and stuff like that, but no NFS, and "Network" only shows Windows Networks.

Maybe NFS isn't installed?   I need to mount an NFS drive under ubuntu, so what do I try next?

---

### Post by blitzer on 2007-04-24
Hi ubnewbie2,

The best I can do is give you a link and hope the info is there for you - Cheers

Keep this in your bookmarks for further help with Ubuntu  :) 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server")

---

### Post by ubnewbie2 on 2007-04-24
> **blitzer said:**
> Hi ubnewbie2,

The best I can do is give you a link and hope the info is there for you - Cheers

Keep this in your bookmarks for further help with Ubuntu  :) 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server")

Thank you, that got me going using the command line. It wasn't the server stuff, but the client stuff I needed btw.  

Still haven't found any GUI support for NFS drive mappings in ubuntu yet though.  Does it exist?

---

### Post by blitzer on 2007-04-25
You are very welcome ubnewbie2 :)     Have you tried Ubuntu search ?  Google search ?  Give that a try and good luck.

---

### Post by BKonkle on 2007-05-05
I use Webmin for exporting and mounting NFS shares.  I love Webmin - it makes things which were previously done only through the console much easier than they were before.

---

### Post by Slim Backwater on 2007-05-06
> **ubnewbie2 said:**
> Still haven't found any GUI support for NFS drive mappings in ubuntu yet though.  Does it exist?

I'll try to explain the difference between NFS and SMB (windows or samba shares) to the best of my knowledge.

NFS doesn't operate at the 'user' level so you can't connect to NFS shares like windows shares.  It's a different paradigm.  NFS shares are mounted into the filesystem at the 'root' level.  SMB shares are accessed on demand and authenticated by the user.

NFS shares are setup by root.  root on the server exports the filesystem, and root on the client mounts it.  Client processes get access if their userid (uid) or groupid (gid) allow them access to the file. (or if the file has world permissions).  This is why uid and gid mapping between clients and servers is so important.  The server doesn't know about usernames on the client, just the uid/gid of the process opening the file.

Getting uids in sync isn't a problem if you're building the whole network security, but for adhoc sharing, it's the pits.

SMB uses user authentication.  A SMB share doesn't exist until the user asks for it (browsing).  When the user wants to access a SMB share, the SMB server asks for authentication (a username/ password).  In a domain environment, the user passes the 'key' that they received when they logged into the domain.  A SMB server that's part of the domain trusts keys issued by the domain controller so users don't see a prompt for a username/password from domain fileservers, but it still happens.

With NFS, you can mount filesystems even when no one is logged on (like when the system is booting) but SMB can't do this.

SMB is more like FTP, NFS is more like mounting a hard drive.  Think about that for a moment.

If you were setting this up within your house (a few of workstations and a server) you'd want to export (via NFS) directories for your linux clients, and share (Samba via SMB) those same directories for Windows Clients.  It's only because Linux clients can connect to Windows shares that there is apparent duplication and confusion of services, but NFS and SMB operate at different levels and accomplish different goals.  (it's hard to remote boot a machine off a SMB share because the boot process has to provide a password to the server)

OTOH, if you were trying to share some files for a LAN party, NFS wouldn't be a good choice at all!  Everyone would be UID 1000 and would have full access to all your files.  Not to forget that each user would have to drop to root (or sudo) to the mount the NFS filesystem.

SMB would be a good second choice for a LAN party, as you'd either have to create a SMB account for each attendee, or a group account, or open the guest account which a SMB client will try before prompting for a username/password.

But the first choice in that situation would be a web (HTTP) share.  Setup Apache and create an Alias for a directory and tell them to use their browser and go to [http://server/share/](http://server/share/).  It's read only, so you couldn't receive files from them, but usually a LAN party is just about the distribution of patches, maps and map packs.

Just to extend the LAN party scenario, if you wanted to give AND receive files, then SMB might be a good choice, but personally I'd setup a FTP share and a group account.

So I hope that helps you out in some way.

._.

---

### Post by bbrand on 2007-05-08
My two cents.

I run a home/office network with windows and Ubuntu machines. My main firewall/router/server is an Ubuntu based machine.

I have tried twice now for implement a stable Ubuntu file server exclusively using SMB based shares. The problem I constantly seem to have (Dapper. Breezy, Feisty ... all of them) is getting the auto mount of public shares stable between a Ubuntu desktop and the Ubuntu based server.  At best this was stable for a few weeks and then after some update the shared would no auto mount any more and create all kinds of issues. This happened again over the weekend and I have now given up on that approach.

I now implemented NFS for the permanent public shares to be done with it. The Samba shares remain for the Window machines and ad-hoc browsing on the Ubuntu side. Both coincide nicely at the moment.

The public shares are wide open on my network ... they are public!! The “downside” that NFS has weaker security does not make sense in my case any one else that has the need for a public share. That is, as long as a decent firewall is deployed.

Ben

---

### Post by ubnewbie2 on 2007-05-08
> **Slim Backwater said:**
> I'll try to explain the difference between NFS and SMB (windows or samba shares) to the best of my knowledge.

NFS doesn't operate at the 'user' level so you can't connect to NFS shares like windows shares.  It's a different paradigm.  NFS shares are mounted into the filesystem at the 'root' level.  SMB shares are accessed on demand and authenticated by the user.

NFS shares are setup by root.  root on the server exports the filesystem, and root on the client mounts it.  Client processes get access if their userid (uid) or groupid (gid) allow them access to the file. (or if the file has world permissions).  This is why uid and gid mapping between clients and servers is so important.  The server doesn't know about usernames on the client, just the uid/gid of the process opening the file.

Getting uids in sync isn't a problem if you're building the whole network security, but for adhoc sharing, it's the pits.

SMB uses user authentication.  A SMB share doesn't exist until the user asks for it (browsing).  When the user wants to access a SMB share, the SMB server asks for authentication (a username/ password).  In a domain environment, the user passes the 'key' that they received when they logged into the domain.  A SMB server that's part of the domain trusts keys issued by the domain controller so users don't see a prompt for a username/password from domain fileservers, but it still happens.

With NFS, you can mount filesystems even when no one is logged on (like when the system is booting) but SMB can't do this.

SMB is more like FTP, NFS is more like mounting a hard drive.  Think about that for a moment.

If you were setting this up within your house (a few of workstations and a server) you'd want to export (via NFS) directories for your linux clients, and share (Samba via SMB) those same directories for Windows Clients.  It's only because Linux clients can connect to Windows shares that there is apparent duplication and confusion of services, but NFS and SMB operate at different levels and accomplish different goals.  (it's hard to remote boot a machine off a SMB share because the boot process has to provide a password to the server)

OTOH, if you were trying to share some files for a LAN party, NFS wouldn't be a good choice at all!  Everyone would be UID 1000 and would have full access to all your files.  Not to forget that each user would have to drop to root (or sudo) to the mount the NFS filesystem.

SMB would be a good second choice for a LAN party, as you'd either have to create a SMB account for each attendee, or a group account, or open the guest account which a SMB client will try before prompting for a username/password.

But the first choice in that situation would be a web (HTTP) share.  Setup Apache and create an Alias for a directory and tell them to use their browser and go to [http://server/share/](http://server/share/).  It's read only, so you couldn't receive files from them, but usually a LAN party is just about the distribution of patches, maps and map packs.

Just to extend the LAN party scenario, if you wanted to give AND receive files, then SMB might be a good choice, but personally I'd setup a FTP share and a group account.

So I hope that helps you out in some way.

._.

That's as may be, nevertheless the help says you can access NFS shares via that gui, but, on my system, you can't.

---

### Post by Slim Backwater on 2007-05-09
> **ubnewbie2 said:**
> That's as may be, nevertheless the help says you can access NFS shares via that gui, but, on my system, you can't.

Ahhhh I see what you're talking about:

Ubuntu Help (System - Help and Support)

Files, Folders and Documents
Working with files
6.11. Navigating Remote Servers
6.11.2 To access network places

> 
If your system is configured to access places on a network, you can use the file manager to access the
network places. 

To access network places, open the file manager and choose Places &#8594; Network Servers. A window opens that displays the network places that you can access. Double-click on the network that you want to access. 

To access UNIX shares, double-click on the Unix Network (NFS) object. A list of the UNIX shares available to you is displayed in the file manager window.

To access Windows shares, double-click on the Windows Network (SMB)  object. A list of the Windows shares available to you is displayed in the file manager window.


Also found here:

[http://www.gnome.org/learn/users-guide/2.6/ch07s08.html](http://www.gnome.org/learn/users-guide/2.6/ch07s08.html)

My guess is that this is functionality that's in the core Gnome Nautilus, but has been configured out of Ubuntu's implementation and the documentation wasn't updated.  Strange that there's this loss of functionality though.

I wonder if there is a package that will add this support.

While researching this, I read something about the 'Gnome Virtual Filesystem' and there is a package with that name that doesn't look like it's installed by default, gnome-vfs-ext 

> 
GNOME VFS is the GNOME virtual file system. It is the foundation of the
Nautilus file manager. It provides a modular architecture and ships with
several modules that implement support for file systems, http, ftp and others.
It provides a URI-based API, a backend supporting asynchronous file
operations, a MIME type manipulation library and other features.


I'll give it a shot and let you know if I see any changes.

._.

*Edit, that didn't make any noticable differences, but I did find this: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/43363](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/43363)
> 
I can go out the the CLI and issue "showmount -e 192.168.1.23" and it displays the available NFS share.


and this: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/24430](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/24430)
> I have the same problem and, for what I've found out, it is related to NFS protocol not being supported by current version of gnomevfs2.
I read somewhere that NFS got dropped switching from gnomevfs to gnomevfs2 and that support is now available only through a patch. I think ubuntu package lacks that patch.

and this: [https://blueprints.launchpad.net/ubuntu/+spec/nautilus-browse-nfs](https://blueprints.launchpad.net/ubuntu/+spec/nautilus-browse-nfs)

Soooo.... it's a bug! :)

---

### Post by ubnewbie2 on 2007-05-10
> **Slim Backwater said:**
> 
Soooo.... it's a bug! :)

Well, that's all right then :) 

Seriously, thanks for the research you did and the answers.

---

