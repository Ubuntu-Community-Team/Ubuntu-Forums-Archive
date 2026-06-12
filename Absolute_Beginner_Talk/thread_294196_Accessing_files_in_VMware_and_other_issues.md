---
title: "Accessing files in VMware and other issues"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-11-06
I've just installed XP Pro under VMware and am a little lost.

Is there a way of accessing files in VMware which are kept in my /home?

It's not able to use my wireless connection, but it can use wired ethernet...

Also, are there any simple tutorial/howto type documents which can teach me simple VMware-ing?

---

### Post by davmac on 2006-11-07
I don't know if it's the easiest or "proper" way, but for transferring file between host and guest I installed an FTP server on the Ubuntu host and and FTP client (FileZilla) on the windows guest. That worked fine. See [http://ubuntuguide.org/wiki/Ubuntu_Edgy#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#FTP_Server) for info about installing the server.

I didn't have a problem getting the networking set up to use my host's wireless connection. I'm on a windows machine at work and so cannot remember the exact option, but if you open the guest's networking properties, it's the choice at the top of the list, that effectively creates you a new IP address on the network. Note: To the guest this looks like a wired connection.

I didn't find any simple tutorials, but managed to find all the answers I needed by either searching for "VMWare" here, or for "Ubuntu" at the VMWare forum.

Hope this helps,

Dave Mac

---

### Post by dmizer on 2006-11-07
do you only have vmware player? or did you comple vmware server?  if you only have vmware player, i'm not sure it will be possible for you to connect to the internet through your xp install.

---

### Post by happy-and-lost on 2006-11-08
I've downloaded VMware server but I have no idea how to install it :(

Sorted the connection in Player, though

---

