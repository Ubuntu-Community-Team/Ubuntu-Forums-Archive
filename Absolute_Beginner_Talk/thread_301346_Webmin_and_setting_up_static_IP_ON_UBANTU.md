---
title: "Webmin and setting up static IP ON UBANTU"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Bill007 on 2006-11-17
kIA ora

REASON

Being new to this and wanting to set up a server for my own purposes and the challenge of it!

I have come along way with the ubantu server setup but have hit a small wall

Every thing is going well UP TO THE downloded webmin part but found I didnt have perl so got that DOWNLOADED and reloaded webmin and it seems to accepted the perl directory

BUT cant reach the server thru my browser the ](*,) ](*,)  network address [http://server1:10000/](http://server1:10000/)

So after some googling it seems i need to set up the static ip address

below is what I have found HOPEFULLY THE PROBLEM

This file describes the network interfaces available on your system

and how to activate them. For more information, see interfaces(5).

The loopback network interface

auto lo
iface lo inet loopback

This is a list of hotpluggable network interfaces.

They will be activated automatically by the hotplug subsystem.

mapping hotplug
script grep
map eth0

The primary network interface

auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

on the command line i type

$ vi etc/network/interfaces

this is the command which opens the network interface settings and i get the screen

This file describes the network interfaces available on your system

and how to activate them. For more information, see interfaces(5).

The loopback network interface

auto lo
iface lo inet loopback

This is a list of hotpluggable network interfaces.

They will be activated automatically by the hotplug subsystem.

mapping hotplug
script grep
map eth0

The primary network interface

auto eth0
iface eth0 inet dhcp

thats fine too I make the changes TO

iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1



but cant seem to save the changes or exit the screen due to not knowing the command to save and exit FROM the ubantu command line

Can anyone help here how do I save the changes and exit the screen to move on to the next part

Kind regards Bill007](*,)

---

### Post by anarky on 2006-11-17
you could also use a free dns service (if im correct) from somebody like no-ip because they it will automatically update to any of your IP changes :X sorry if im wrong

---

### Post by Bill007 on 2006-11-17
Ok but how does one introduce no-ip type dns to the ubantu command line:confused:

---

### Post by CatKiller on 2006-11-17
You could use **nano** instead of **vi**. It's a much more "user-friendly" editor than vi.

Also, you'll need to use **sudo** in front of any command that involves writing somewhere other than your home folder:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

I don't know anything about networking setup from the command line though.

---

### Post by jkroto on 2006-11-17
> **Bill007 said:**
> Ok but how does one introduce no-ip type dns to the ubantu command line:confused:

I think you can
```
sudo apt-get no-ip
```

You need to setup an account with no-ip first.  after it installs then you must 
```
sudo no-ip -C
```
this is to configure.

I used this [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS) to figure it out.

Hope this helps.

---

### Post by lazyart on 2006-11-17
Using no-ip is fine if you want to access your server from outside of your network... but that will not help you at all trying to set a static ip to work with from a machine on your network.

Use Catkiller's advice and use nano instead of vi.  Once that's done and you reboot you should have the static address you are looking for.

---

### Post by Bill007 on 2006-11-17
Thanks  for that info 

First things first to get static ip sorted so i can see webadmin  in a browser 

Just for the record 

this is the setting currently

The primary network interface

auto eth0
eth0 inet dhcp

Is this what the setting needs to be changed to 

auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

Other then that thanks for the command line info
 and the xtra advice 

Kind regards Bill007

---

