---
title: "Sharing one printer with two Ubuntu 7.10 computers."
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2008-01-01
Please forgive my cross post but I place this question in what may have been the wrong Ubuntu forum.  Anyway back to my problem:

I read for much of the afternoon about sharing a printer on two Ubuntu 7.10 computers but I've failed to get them to work on both machines.

Following the route

System>adninistration>printing and selecting> server settings>"Share published printers connected to this system" - on the computer connected to the printer (server)

Then on the other computer I wish to share the printer with I go to:

System>administration>printing and selecting> server settings>"Show printers shared by other systems" and then add the printer and its url but this does not allow me to network the printer.

The printer works fine on the server computer but will not on the other.

How else can I do this please?

---

### Post by cmnorton on 2008-01-05
On the server, you'll need to set up SAMBA. I do this so infrequently that I cannot remember all the steps:

Here is an example out of one of my /etc/samba/smb.conf files, and it's from Fedora, not Ubuntu. 

So, these samba changes would be on the server:

# workgroup = NT-Domain-Name or Workgroup-Name, eg: MIDEARTH
	workgroup = your-windows-domain

# server string is the equivalent of the NT Description field
	server string = samba %v server

	default service = printers
	netbios name = your-servers-name

You'd be best to browse through and and experiment with the settings in that file, and also on your client set up a printer that is an smb printer (on the server). I believe you have to restart samba after you've made smb.conf changes.

---

### Post by astoltz on 2008-01-05
You only need SAMBA if one of the machines is running Windows.  Since they are both Ubuntu, it's actually CUPS that is doing the sharing.  What you have done should be OK.  On the network machine, does thet printer even show up in the list?

---

