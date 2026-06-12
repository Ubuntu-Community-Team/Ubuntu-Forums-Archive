---
title: "Is this possible?"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by SpawnSC on 2006-08-01
Would there be a way to get my home ubuntu desktop on my ubuntu laptop at work?  Like a roaming profile.. what changes I do on my work laptop is reflected back to my home desktop? make sense:confused:

---

### Post by nalmeth on 2006-08-01
VNC might be an option, but I'm not sure if it will do exactly what you're looking for.

It's a remote desktop tool

---

### Post by stupidkid on 2006-08-01
Or just ssh?

---

### Post by T700 on 2006-08-01
I don't think it's possible.  The only roaming profiles I've seen implemented were on the same network.  For instance, if I normally logged into my PC in my office at the pharmacy department, I could log into a PC in ER and get my own apps and layout delivered to me.

Maybe someone else will have a better idea.  Stay tuned.

Paul

---

### Post by Macchi on 2006-08-16
I would be also very glad to find a good solution for roaming profiles on Ubuntu Servers plus Client Desktops. 
Presently I have been working with two solutions for sharing information and desktops:

1) A central FreeNX server that provides very efficient, safe, and cheap remote desktops. The NX protocol is similar to VNC and Windows' remote desktops but it compresses very efficiently (X) graphics and encrypts the communication through ssh. The FreeNX client can be run from all platforms and any computer with (ssh) access to the internet.
For instance, I can use a remote desktop with persistent sessions on my server through a 3G mobile internet connection on my laptop. The server only needs one hidden ssh port open to the internet, LAN or WLAN.


2) Primirily I use a combination of sshfs and rsync, where I access my home+shared files through sshfs and synchronize files in the background between my laptops and other desktop computers. Thus I spread copies of information on different computers, (server+desktop+laptops). This is inefficient but creates backup copies that are always ready to use despite most potential failures on single computers. This approach has drawbacks, like requiring some manual interaction, but it is simple and quite reliable.

I have previously used roaming profiles on a samba server together with Windows clients, thus always bringing up the same environment on different computers, but gladly I have now moved completely to open source software. Previoulsly I also used NFS for file sharing on Linux but I still find difficult to get a reliable and simple solution for remote authentication and data sharing.

---

