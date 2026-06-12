---
title: "Ubuntu Router HELP!!! (Masquerade)"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2006-10-03
Edit: I got this working I posted my solution it's then third reply, forth entry.


Ok so I have got a ubuntu machine with two nixs. eth0 and eth1

eth0 has my cable internet pluged into it
eth1 is pluged into my switch where there are a bunch of other computers.

I have spend lots of time and have managed to get my ubuntu machine talking to the internet. but I can get it to talk to the other machines!!!

In trying to I have ended up installing the xubuntu-desktop package and webmin! but still on luck.

I did not want to have a GUI but now is there I'll keep it for the mean time

I need this machine to do dhcp and let my other machines on the net etc. The reason i'm using ubuntu is because there are other things I want to do and can.

I've seen some how to's and they just make me real lost so if anyone can help me out that will be awesome.

---

### Post by tagra123 on 2006-10-03
This may help.

[http://www.linuxquestions.org/questions/showthread.php?t=319188](http://www.linuxquestions.org/questions/showthread.php?t=319188)

---

### Post by guysmiley25 on 2006-10-03
Thanks I'm still quite lost. Think I need someone to hold my hand lol.

My machines can see each other I did this by setting the IP on then manully but I still can't use the internet.

---

### Post by guysmiley25 on 2006-10-04
Ok I got it working so just incase there was someone else trying to do the same there i'll explain what I did.

First what I was trying to do is setup a ubuntu server. I used to have clarkconnect but I wanted to do more things so yeah

So this is what you do if you have a computer and need it acting as a router don't want a gui but you still can. and need ubuntu cause things like clarkconnect make it harder to do more things. LDAP etc.

My setup was

Cable Internet --> Ubuntu Server --> Switch --> Other computers lin/win etc

Ok first thing. if you don't want a GUI grab a ubuntu/kubuntu or whatever alternative disc from somewhere.

Pop it in a boot it up

If don't want GUI so install server, else just normal install.

I unpluged my network cable during install so that during the install it will ask me to setup the networking. I seleted do not config networking now or whatever it is.


Tip: I cheated and booted to a live cd of xubuntu and mounted the hard drive so that I could copy paste from the net etc. To do this. From the live cd go.

$ mkdir server
$ sudo mount -t ext3 /dev/hda1 server

where my server was installed on the first parition of the first hard drive.


After it is install login as you do.
To get your internet working for the server and setup the other network card go.
$ sudo nano /etc/network/interfaces

My setup looked a bit like this

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address <ip address>
netmask 255.255.255.0
gateway <gateway>

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

where eth0 was for internet
and eth1 was for switch
<ip address> given by ISP
<gatewasy> given by ISP

you may have to play around with this a bit. I did.

You can now test your internet connection if you know an IP for something. you may need to restart

now we setup the dns servers part.

$ sudo nano /etc/resolv.conf

Mine looked like

nameserver <dns 1>
nameserver <dns 2>

<dns 1> and <dns 2> is given by ISP

ok now you can test your internet you may need to restart

$ ping google.com

Now that part should be sweet.

Now lets add some extra repositories
see

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

pretty much put what they have in your /etc/apt/sources.list

after that go
$ sudo apt-get update

should be good

now it would be a good idea to install ssh so you can access you box. maybe not so if you have a GUI but I probably would.

$ sudo apt-get install ssh

Now to make it so the other computers on the network can access the internet I used this guide, they say to not use sudo but I did and it worked so i'm not too sure about that

[http://doc.gwos.org/index.php/Share_Internet_Connection](http://doc.gwos.org/index.php/Share_Internet_Connection)

then do dhcp so that other machines on the network get an IP

[http://ubuntuguide.org/wiki/Dapper#DHCP_Server](http://ubuntuguide.org/wiki/Dapper#DHCP_Server)

Hope that covers it all. any quesitons just ask.

---

