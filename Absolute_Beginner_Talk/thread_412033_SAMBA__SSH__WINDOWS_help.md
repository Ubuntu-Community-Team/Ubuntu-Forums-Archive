---
title: "SAMBA / SSH / WINDOWS help"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by jcws6 on 2007-04-17
I have been searching a whole day for a solution for my problem, and I've found many... but I'm looking for the EASIEST and the BEST way.  I've only been using Ubuntu for about 4 days now, so I apologize if I've missed something glaringly obvious.

Here's what I'm looking to do - access a file share (on my Ubuntu box) securely, from any Windows computer, anywhere.  I want to be able to map a network drive to the share, or open a shortcut to it.  I'll eventually use the RSA security, but username/password is fine for now.

Here's what I've done so far - I've got a DynDNS hostname, with a hardware IP updater client on my router.  I set everything on my network with static IPs & enabled port forwarding for SSH & VNC on my router.  I configured Samba, and I was able to open & write to the folder on my server from another PC on my network.  Then I installed Firestarter & opened up incoming ports for SSH & VNC.  Then installed the newest version of OpenSSH on the Ubuntu box.  I changed the SSH port (which was also changed in my router's port forwarding & in Firestarter), disbled root login, and added my system account as the only user.  I was able to SSH to it via PuTTY from a Windows PC on my network.

Now for the big question - what do I need to do to open the file share in Windows after I get the SSH tunnel established with PuTTY?  I've read all kinds of info about SSHFS and SFTPDrive and disabling Windows Networking - but all of this seems like a lot of work.  Is there an easy way just to map a drive to the server thru the SSH tunnel?

Sorry for the long post, but I tried to be detailed.  Thanks in advance for any help!!

---

### Post by jcws6 on 2007-04-17
Well, I just noticed glaringly obvious mistake #1.  I'm going to shut down my VNC ports & funnel VNC traffic thru the SSH tunnel.

Any ideas on that one, as well?

---

### Post by jcws6 on 2007-04-17
Alright, I've got my VNC question solved.  Here's what I'm doing (from the remote Windows PC):
1. Create a new PuTTY tunnel (source = 5900, destination = 127.0.0.1:5900)
2. Open PuTTY, connect to Ubuntu server
3. Open VNC viewer, connect to 127.0.0.1:5900

That wasn't too bad.  I'll test this out tonight.  Do I need to do anything with port 5800?  Any ideas on the original SSH question?

---

### Post by wormser on 2007-04-17
Just for your knowledge.  This is how you would set up a tunnel threw a shell.

**ssh -L xxxx:localhost:yyyy [email]username@domain.com[/email]**

In your vnc viewer **localhost:xxxx**

x = your local port
y = remote port for vnc server

---

### Post by scrooge_74 on 2007-04-17
i used to use this solution when I had an XP machine [http://b-l-w.de/sambassh_en.php](http://b-l-w.de/sambassh_en.php)

---

### Post by jcws6 on 2007-04-22
Here's what I have working right now - SSH internal/external, VNC internal/external, network share internal.  The only thing I can't get working is accessing the network share outisde the network.  I'm using the Loopback Adapter method, and every time I try to map a network drive to the Samba share from outside of my network, I get this error:  "\\10.0.0.1 is not accessible.  You might not have permission to use this network resource.  Contact the administrator of this server to find out if you have access permissions.  The network path was not found."

Any ideas?

---

### Post by jcws6 on 2007-04-22
Is there any way I can move this post to the "Networking & Wireless" or "Servers & Security" Forum, in hopes of a better answer?

---

### Post by mrfreddy on 2007-04-23
> **jcws6 said:**
> Here's what I have working right now - SSH internal/external, VNC internal/external, network share internal.  The only thing I can't get working is accessing the network share outisde the network.  I'm using the Loopback Adapter method, and every time I try to map a network drive to the Samba share from outside of my network, I get this error:  "\\10.0.0.1 is not accessible.  You might not have permission to use this network resource.  Contact the administrator of this server to find out if you have access permissions.  The network path was not found."

Any ideas?
I'm trying to do something very similar. I haven't got it working perfectly but [**this**]("//http://lists.samba.org/archive/samba/2007-March/130088.html") might of some use.
[URL="http://www.blisstonia.com/eolson/notes/smboverssh.php"]
**This**[/URL] article is what got me started.

---

### Post by jcws6 on 2007-04-23
Thanks for the help everyone, but luckily I'm much smarter than I was 5 days ago.  

Here's how my setup's going to be now:  all firewalled, VNC & SMB direct access from internal network, VNC & SMB access via VPN from outside of my network, and SSH for external web proxy.  Right now, I have 2 out of 3 done.  I've found that I like SSH, but I don't like having to disable Windows File Sharing or enable a "virtual adapter" every time I want to mount a share in Windows.

So, now I'm off to learn everything I can about OpenVPN (suggestions welcome).  As soon as I get everything set up & working, I'll submit a complete start-to-finish HOWTO on how to configure Ubuntu as a secure NAS.

---

### Post by huotg01 on 2008-03-21
JC

How did you finaly manage to get Samba connection from external. I can't.

G.

---

