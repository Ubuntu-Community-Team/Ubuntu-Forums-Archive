---
title: "Can I backup my home network without a GUI?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by tudedude on 2006-08-02
New Linux user. I just installed Ubuntu 6.0.6 LTS Server on a system. I currently have a command line interface only. Our other machines have Windows XP. (1 with Pro and 2 with Home Edition) on a home network with DSL and a wireless router\switch.

The main thing I want this Linux machine to do is to perform backups of my Windows machines on disk. I understand I need to install SAMBA to communicate with the Windows systems. 

I really don't want this Linux machine to communicate with the outside world (Internet) unless that's the only way I can do this.
 
I just want this machine to be available internally within my home network and just be a place where I can do backups of my Windows machines. 

Can this be done with just a command line interface? I have read about the backuppc application, but that seems to require a graphical interface to be installed although backuppc seems to  be what I am looking for.

---

### Post by scxtt on 2006-08-02
i see no reason why you can't install samba, mount some Windows XP shares, then get cron jobs to 'archive' whatever you want ... as far as the internet goes - it'll be plugged into your router, and will have access to the internet, but don't forward any ports to it (sure, it can get 'out', but outside things can't get in) ... unless you feel like spending xtra cash on a hub and xtra NIC cards (seems silly to me) ...

---

### Post by tudedude on 2006-08-02
Thanks, I guess step 1 will be to install SAMBA and try to get that to work. I will probably have to put another post on 'what am I doing wrong with SAMBA?' :)

---

### Post by Dr. Nick on 2006-08-02
You could also setup a ftp server on the linux machine in a command line, If you did this I wouldnt have it hooked up to external internet though. 

Are you using a 3rd party backup application on windows and just looking for a place to store "images", or are you looking for your linux box to automatically backup the other hard drives?


Ftp servers are easy to setup, If you run a backup application on windows you could just place the backup onto the linux computer by ftp, If you are after a automated system I am not sure

---

### Post by tudedude on 2006-08-02
Thanks for the input. I want the Linux box to automatically backup my other machines.

---

### Post by tudedude on 2006-08-03
I've managed to install Samba. I can see my linux box on my windows network. I mapped a drive to a folder on the linux box and was able to copy a file to it.

So for security. Again I want to keep the outside world completely out but want my machines inside my home network to communicate with the Linux box. The Linux box is connected to my wireless DSL router\gateway (Belkin Pre-N) I use MAC address filtering for my wireless systems. It was mentioned to forward ports for this box and allow the system to get out but no access in. How do I do this?

---

### Post by Dr. Nick on 2006-08-03
All the port fowarding is done within the router, each router is different.

However port forwarding is mainly used on communications from the outside in, I am not sure how it could be used to allow a system access to the internet but not recieve incoming, As far as I know its either access in and out, or no access in or out, cant have one without the other.

I think some routers have access controls which you may be able to setup via mac or satic ip address to restrict when the system has access to the internet, You may just need to mess around inside the router some and see what all options it gives you as far as access control

---

### Post by tudedude on 2006-08-03
Thanks, I will see what I can do with the router.

---

### Post by Dr. Nick on 2006-08-03
Another thought I had just now, Never done it before so you might have to research it a bit to get it working.

Linux has a built in firewall called iptables, You could most likely configure it to block every connection on every port expect for those you specify. You could then specify that it is only allowed to accept connections from the ip address on your lan and only on port 139 (I think samba is 139, could be wrong though) This should also do a pretty decent job of blocking any unauthorized access from the outside

---

