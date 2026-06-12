---
title: "n00b + need to prepare = asking you for advice :)"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by z33k3r on 2006-06-17
Hey guys, you guessed it... another n00b! So I might as well ask the question that is bouncing around in my mind as I jump into Linux...

Soon, hopefully, my church will be starting a small school. I and another guy will probably be in charge of setting up a network of computers for the teachers and students etc. So this is what I am thinking my setup is going to look like. Please feel free to tell me that I am wrong and how to go about it correctly...


[Outside World]
------V------
[DSL Modem]
------V------
[Firewall/Router] - Ubuntu Server
------V------
[NFS/Web/Email] - Ubuntu Server
------V------
[Network Switch]
------V------
[User Network] - Edubuntu or Xubuntu - (probably 5-10 desktops to start)


Now, I would like the users to have roaming desktops and network printer sharing. Also would like the students and staff to be able to work from their home M$ systems via a VPN or such.

The building was a school before we bought it, so everything is pretty much all ready wired with CAT5 :) I was also possibly entertaining the idea of, down the road, building a media server to stream content to each of the rooms' TVs! But anywho... 


So, here are my questions...

-Has any body done something like this? and what where your experiences?

-I am planning on setting up my house this way as well so this should be a good starting point. Where should I start first? The server? The desktops?

-Once I have a intallation on a system that I like and has all the software etc, how do I go about distributing that image to the rest of the systems as they would more than likely have different hardware..?


I apreciate anybody that takes the time to answer my questions! :KS

---

### Post by jeroen2 on 2006-06-17
z33k3r,

You sure don't sound like a n00b to me! More like a poweruser learning a different platform..

I can't answer all your questions. I'll try with some:

> -Once I have a intallation on a system that I like and has all the software etc, how do I go about distributing that image to the rest of the systems as they would more than likely have different hardware..?

You can use kickstart to install quicker and still have ubuntu recognize different hardware:
[https://wiki.ubuntu.com/KickstartCompatibility](https://wiki.ubuntu.com/KickstartCompatibility)

Ghostlike images can be made and distributed using partimage ```
sudo apt-get install partimage
```.

It's also possible to build a local network repository using apt-move. Follow the apt-move howto at:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

For VPN-like acces you van use VNC or rdesktop from the repositories.

If I were you, I'd start with an inner server and a desktop so you can test machines you add to the network.


Hope this is helpfull,

~Jeroen

---

### Post by Spleenie on 2006-06-17
My suggestion is that you ask this question in the server talk category. The people who read that forum may have the particular expertise that you need.

---

### Post by blkish on 2006-06-17
hi

i agree, server talk would be a good place to get more info about this.

you might also like to look into other 'turn-key' style distributions for your firewall/router. 

m0n0wall - [www.m0n0.ch](www.m0n0.ch) is an excellent firewall/router platform built on FreeBSD that is extremely reliable (esp. when run off compact flash or even bootable CD + floppy for configuration).
it also has good VPN capabilities

there are also some good articles/how-tos out there regarding good practice and setup of perimeter servers within an environment such as the one (i believe) you are describing.

let me know if these would be of interest.

good luck with your project,

blkish

---

### Post by IYY on 2006-06-17
Maybe Ubuntu is not the best idea for the Firewall and/or mail server. There are many tiny Linuxes and BSDs that do these things out of the box because they are designed for it, and don't do anything else. Not that it would be complicated to set up with Ubuntu, but it's a bit of an overkill.

---

### Post by z33k3r on 2006-06-17
jeroen2 -

Yeah, your right, I was just mentioning that I am a *nix n00b :) I can do anything on a M$ box, but I am looking for a secure and free solution!

With Kickstart, I would be able to pop in a live cd and install from a network image, using a Kickstart file to answer all the installation questions... like which software to install, network settings, etc...?

I am thinking apt-move wouldn't work due to the likelyhood of the machines being built with different hardware...right?

As for the VNC/rdesktop idea, the user's will more than likely have M$ at home. I am not looking to use a remote desktop, just the availability of their files from school... but at home.



blkish - 
m0n0wall looks pretty new..? Have you used it? if so how did you like it compared to other solutions? 

Those articles sound interesting! Are there any that cover the entire gammat or specific articles that would help me out?


IYY - 
What other stable solutions would you recommend?

---

### Post by brentoboy on 2006-06-17
I would suggest edubuntu.  It uses LTSP the Linux Terminal Services Project.

you set up your edubuntu server, use the wiki to get it all running, then add users and you are done.

the clients dont even need to install anything, you can remove thier harddrives if you want.  all you need as about 128 mb of ram, a processor (any old 386 or better will do) and a monitor.  oh, and you need onboard lan.  your bios needs to be able to boot using pxe (most with onboard lan work)  if you dont have onboard lan, it can still work but it takes a little while to set them up (the ones that boot to pxe just work)

then you have roming desktops.  the way ltsp works is like so:
the server is running using dhcp, ltsp, nfs, and tftp (the terminal server, the network file system server, and a trivial ftp server.

the clients boot up and using the pxe protocol, ask for an ip address.
your server gives them one, and as part of the process, they handshake, and use tftp to download a minimal kernel from the server.
it puts it in a small ram disk that it pulls from the client's ram.

then, the client boots to the kernel, and once it is semi functional, it connects to the server by mounting a root file system that shared from the server via nfs.

once a filesystem is mounted, it boots up into xwindows. That ends up being the only signifiant application actually running on the client PC.

it uses the client-server options built into xwindows to connect its session to the server.  so the server runns all the programs (including gnome, and everything else) as though the client was indeed running on the server.

users login, do stuff, log out, go to a different client, log in, and thier prefereces just work, it is as though you have exactly one pc, but everyone can use it at the same time.

updates are easy.  you dont have to even touch the clients.  you update the server, it runs a script that updates the root folder that is shared for the clients -- boom everything is up to date.

I use it for a small computer lab that I have for my extended family.  It lets my friends and family come in, select the "best" computer that isnt already in use, and no one can complain that they "need" a particular pc becuase everythign is stored on the server.

---

### Post by blkish on 2006-06-18
hi again

m0n0wall has been around for quite some time now and is extremely stable. i've used it for some considerable time both as a home/SOHO router and in ISP scenarios routing backbone traffic.

never been anything but pleased with its performance. 
it's a very clean solution to the 'i need a flexible, open-source enterprise-class firewall', IMO

there is a much newer port of m0n0wall - pfsense - which is not quite production ready yet (needs some more field testing). you might like to track the progress of this distribution as well as it's very promising for the future.

however for the moment, based on the requirements you outlined in your first post, i'd say m0n0wall would be ideal for your environment.

regarding the articles, in particular i'd recommend [this one]("http://www.hornfordassociates.com/pages/documents/howto/linux/perimeter_centos_howto-1.html") and the debian version [here]("http://www.hornfordassociates.com/pages/documents/howto/linux/openvpn_howto-1.html").

the above cover the setup of a CentOS or Debian -based perimeter server in an SME environment. you can easily translate the steps+recommendations to ubuntu. it is the sound approach to package management and system TCO (ie, how long must we spend tinkering daily to retain a robust infrastructure) which is of most interest here.

let me know if you'd like any more information about any of the above.

best wishes

blkish

[QUOTE=z33k3r]jeroen2 -

Yeah, your right, I was just mentioning that I am a *nix n00b :) I can do anything on a M$ box, but I am looking for a secure and free solution!

With Kickstart, I would be able to pop in a live cd and install from a network image, using a Kickstart file to answer all the installation questions... like which software to install, network settings, etc...?

I am thinking apt-move wouldn't work due to the likelyhood of the machines being built with different hardware...right?

As for the VNC/rdesktop idea, the user's will more than likely have M$ at home. I am not looking to use a remote desktop, just the availability of their files from school... but at home.



blkish - 
m0n0wall looks pretty new..? Have you used it? if so how did you like it compared to other solutions? 

Those articles sound interesting! Are there any that cover the entire gammat or specific articles that would help me out?


IYY - 
What other stable solutions would you recommend?[/QUOTE]

---

### Post by z33k3r on 2006-07-07
Brentoboy,

That sounds great, a roaming desktop on steriods! My old office did that with the tech machines that we used, but they always seemed slow. 

What is the boot up time and do you have any issues with lag? I am assuming they all have folders setup on a drive somewhere for user settings and file storage... was the whole thing easy to setup? Is there a GUI based administration of this or is it all promt based?

 Also what kinda specs are you using for the server? Does the server ever have bogdown issues? Sorry, just the normal questions... :)

So with that sounding like a great option, should this be my setup:

----------------World
------------------|--
---------------Firewall (monowall or equiv)
------------------|--
--------------DNS Server (what do you guys use?)
------------------|--
---------------Switch
--|---------------|----------------|------
Web Server - Email Server - Network Server (kubuntu)
-----------------------------------|--
---------------------------------Switch
-----------------------------------|--
-----------------------------User Machines


> **brentoboy said:**
> I would suggest edubuntu.  It uses LTSP the Linux Terminal Services Project.

you set up your edubuntu server, use the wiki to get it all running, then add users and you are done.

the clients dont even need to install anything, you can remove thier harddrives if you want.  all you need as about 128 mb of ram, a processor (any old 386 or better will do) and a monitor.  oh, and you need onboard lan.  your bios needs to be able to boot using pxe (most with onboard lan work)  if you dont have onboard lan, it can still work but it takes a little while to set them up (the ones that boot to pxe just work)

then you have roming desktops.  the way ltsp works is like so:
the server is running using dhcp, ltsp, nfs, and tftp (the terminal server, the network file system server, and a trivial ftp server.

the clients boot up and using the pxe protocol, ask for an ip address.
your server gives them one, and as part of the process, they handshake, and use tftp to download a minimal kernel from the server.
it puts it in a small ram disk that it pulls from the client's ram.

then, the client boots to the kernel, and once it is semi functional, it connects to the server by mounting a root file system that shared from the server via nfs.

once a filesystem is mounted, it boots up into xwindows. That ends up being the only signifiant application actually running on the client PC.

it uses the client-server options built into xwindows to connect its session to the server.  so the server runns all the programs (including gnome, and everything else) as though the client was indeed running on the server.

users login, do stuff, log out, go to a different client, log in, and thier prefereces just work, it is as though you have exactly one pc, but everyone can use it at the same time.

updates are easy.  you dont have to even touch the clients.  you update the server, it runs a script that updates the root folder that is shared for the clients -- boom everything is up to date.

I use it for a small computer lab that I have for my extended family.  It lets my friends and family come in, select the "best" computer that isnt already in use, and no one can complain that they "need" a particular pc becuase everythign is stored on the server.

---

### Post by rccharles on 2006-07-07
> **z33k3r said:**
> 
[Outside World]
------V------
[DSL Modem]
------V------
[Firewall/Router] - Ubuntu Server
------V------
[NFS/Web/Email] - Ubuntu Server
------V------
[Network Switch]
------V------
[User Network] - Edubuntu or Xubuntu - (probably 5-10 desktops to start)

I believe that DSL has a fast download speed and a slow upload speed.  You'll want to check.
> **z33k3r said:**
> 

Now, I would like the users to have roaming desktops and network printer sharing. 

In Linux, each user gets a root directory in the /home directory.  All user data and defaults are stored in the user's root directory or subdirectory.  You can use nfs, network file system, to share a collection of root directories.  When the user logs on, the user will get his or her root directory. 

There is no registry in Linux. Almost everything is stored in text files;) 
> **z33k3r said:**
> 
Also would like the students and staff to be able to work from their home M$ systems via a VPN or such.


This is doable.  

> **z33k3r said:**
> 

So, here are my questions...

-I am planning on setting up my house this way as well so this should be a good starting point. Where should I start first? The server? The desktops?

-Once I have a intallation on a system that I like and has all the software etc, how do I go about distributing that image to the rest of the systems as they would more than likely have different hardware..?


 :KS
It doesn't take that long to install Ubuntu.  See this blog:
[http://rhosgobel.blogspot.com/2006/06/installing-ubuntu-comparison-of-ubuntu.html](http://rhosgobel.blogspot.com/2006/06/installing-ubuntu-comparison-of-ubuntu.html)

I suggest checking out some books from your local library on Linux. You may not find something on Ubuntu, but Ubuntu is based on Debian, so Debian will be fine for system administration.

Robert

---

