---
title: "how to see nfs shared folder from client"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by badperson on 2008-03-20
I went through the chapter in the "ubuntu bible" that explains how to set up an nfs server, but I don't know how to view the  shared folder from the client machine. 
 
In the shared folder settings I chose "specify network" and I entered 192.168.0.0/255.255.255.0 (as he had in the book) These are generic ip's, no? 

should those values be the ip of the host?
bp

---

### Post by Mustard on 2008-03-21
I just setup a NFS server the other day, maybe I can help.  I did it all via directly editing the config files rather than using the 'Shared Folders' option in the admin menu.

This is a post I made in relation to my setup...
[http://ubuntuforums.org/showpost.php?p=4556677&postcount=3](http://ubuntuforums.org/showpost.php?p=4556677&postcount=3)

How many machines do you have on your network?

I gained some insight into the process after reading this ..

[http://tldp.org/HOWTO/NFS-HOWTO/index.html](http://tldp.org/HOWTO/NFS-HOWTO/index.html)

My take on the process was that you setup /etc/hosts.deny to deny all IP's initially, then use /etc/hosts.allow to specify the IP's that will be exempt from the hosts.deny.  Then you setup the /etc/export to share the particular folder/s you want specifying the IP or IP range that you will allow access and whether they can read/write or read only. All this was on the server machine.

Then on the client machine you mount the remote shared folder using the mount command or for a more permanent solution via fstab settings.  I also had to allow the IP's of the client and server machines through my firewalls on each machine.  I don't have much experience with firewall configuration though, so I don't know if I did it correctly or not.  It works though.  The only real issue I have struck is that I sometimes have to start the nfs server manually to get it working.  I must have missed something along the way with regards to making it run at startup.

---

### Post by badperson on 2008-03-21
great, thanks for the info. 
I'll look this stuff over during the weekend. 
bp

---

### Post by badperson on 2008-03-27
Hi,

I'm working my way through the HOW-TO link above,and I'm in this section:

4.1. Mounting remote directori
(this is for configuring the client)
In the terminal from the /home directory I type: 

mount [ip of server] [shared folder] and get this error: 
mount: only root can do that

any idea how to get around this? Want to make sure I have that resolved before I start editing the /etc/fstab file, and so on. 
thanks, 
bp

---

