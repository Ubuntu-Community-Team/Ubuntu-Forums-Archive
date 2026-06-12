---
title: "Networking two or more Linux machines"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by gusb74 on 2007-10-17
I'm trying to network two computers - my desktop and my laptop. The desktop is connected by cable to a router/DSL modem (192.168.1.1), and the laptop is connected wirelessly.

The desktop machine has a fixed IP address, but I want the laptop to get its address from the router.

On the laptop, I've added 192.168.1.2 <desktop> to /etc/hosts and I can ping the desktop computer using both the hostname and the IP address from the laptop, but I cannot ping the laptop's hostname from the desktop! 

Apart from giving the laptop a fixed IP and adding it to /etc/hosts on the desktop, is there any other way I can get the desktop machine to see the laptop on the network?

Thanks in advance!

---

### Post by scrooge_74 on 2007-10-17
Ok, the router is asigning a static IP to one and an automatic to the other

[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)
[http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by jimrz on 2007-10-17
Simple way is to go into your router and use it's "address reservation" (or words to that effect) function and reserve the address you want for your desktop. The router will do this by a combination of computer name  and mac address. Then change your desktop to "acquire ip address via dhcp" (the router will still give it the one you reserved). 

You can also reserve an ip for your laptop. Quite handy for home networking, yet still using dhcp so you don't have issues when you take the laptop elsewhere.

I use this method for assigning addresses for all my boxes (1 server, 3 desktops and 2 laptops) and get all the benefits of static ip's on my home network while still utilizing dhcp.

---

### Post by gusb74 on 2007-10-17
> **jimrz said:**
> Simple way is to go into your router and use it's "address reservation" (or words to that effect) function and reserve the address you want for your desktop. The router will do this by a combination of computer name  and mac address. Then change your desktop to "acquire ip address via dhcp" (the router will still give it the one you reserved). 

You can also reserve an ip for your laptop. Quite handy for home networking, yet still using dhcp so you don't have issues when you take the laptop elsewhere.

I use this method for assigning addresses for all my boxes (1 server, 3 desktops and 2 laptops) and get all the benefits of static ip's on my home network while still utilizing dhcp.

First of all, thanks for the very quick replies, guys! 

There's not much I can do with the router - I can set the DHCP start and end addresses and change the IP of the router itself, the netmask and the broadcast address. The router was supplied by the ISP and isn't very configurable. 

I've been following the links from the original reply, but I'm afraid I'm still not much the wiser. I understand that Samba is useful for sharing files/printers etc with Window$ machines, and I have successfully tried this, but is it necessary when both machines are running Linux? 

In one of the links there was a reference to Winbind - is this independent of Samba, or part of it?

---

### Post by scrooge_74 on 2007-10-18
You don't need samba for Linux to Linux, it is main use is to be able to share folders with Win Machines, in the long run you will abandon using samba for linux to linux, you can also connect using the optio given in the top bar for connecting to server and using ssh as the option (sorry don't know the specifics since I am using xfce4 instead of Gnome), you can alsotry nfs.

As for winbind is independent of samba, it just let you communicate better with Win machines in a network enviroment

---

### Post by gusb74 on 2007-10-18
Thanks for the input guys. I still can't get it to work, so I've just assigned static IPs to everything for now. I'm going to sit down with a nice malt later on and get down to some serious reading!

---

