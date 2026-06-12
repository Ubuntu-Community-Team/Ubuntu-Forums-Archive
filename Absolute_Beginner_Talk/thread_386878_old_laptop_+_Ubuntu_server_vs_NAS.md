---
title: "old laptop + Ubuntu server vs NAS"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by zantzinger on 2007-03-17
I was thinking of buying a NAS (Slug or Linkstation) to function as a) a media server hacked with SlimServer to stream music to a Squeezebox 3 and b) to back up files from 3 computers on a home network with some basic scheduled utility. **Then I thought why not use Ubuntu Server on an old laptop** - Dell 5000e, 700MHz PIII, 256MB RAM, 20 GB hdd (but I'd buy a new 120GB IDE hdd). The spec is better than either the NSLU2 or the Linkstation and just getting new hard drive would cost much less than a NAS. Plus SlimServer runs slowly on the Slug apparently and I've heard the LS Pro is a hassle to hack. The only disadvantage I see is higher power usage. But then I'm a complete newbie so please correct me.

I've never used Linux but I've been reading a fair amount recently. Still pretty much at sea, but the way I see it, I'd do a LAMP server install and then the only further packages I'd need to install would be:
SSH
Samba
SlimServer

I probably wouldn't even need the LAMP install because I don't need to use it as a web server yet.

My questions are
Is this way easier and less hassle?
Are there any other packages I'd need to install and configure?

---

### Post by LanDan on 2007-03-19
if you would like to have an easy network storage thing than i would suggest FreeNAS.

but verry well possible to use ubuntu and maybe a good idea to get aquinted with it since you would like to have more options later on.

don't know about slimserver (maybe someone else?)

but samba would be all you need if you want to serve files to some windows boxes over the local network (if no windows you would want NFS)

LAMP would install Apache MySQl and PHP, and i don't think thats what you want but you could add it later on any way. if you decided to host your own website apache will be enough, mysql is a database and PHPis a scripting language that can be embedded into HTML.

ssh is nice if you want secure access to your box, from a remote computer, otherwise better not to have the option,

so, i would suggest doing a minimal install without the LAMP and add the samba package after installation, offcourse you can add all the rest later if needed.

---

