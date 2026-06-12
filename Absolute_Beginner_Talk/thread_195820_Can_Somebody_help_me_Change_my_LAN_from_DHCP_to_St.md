---
title: "Can Somebody help me Change my LAN from DHCP to Static?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-06-13
Hello All!

I would like to change my DHCP LAN to Static...

I have never done this before & I would like your help with this...

Basically, I have a "US Robotics 9107 ADSL 4-Port Router" & 2 Ubuntu Dapper v6.06 Desktop PCs connected to that Router...

I will need your help on HOWTO change/set my Router & 2 Desktop PCs from DHCP to Static...

To do this, I have taken some snapshots of my Router's Menu Options...

Here it goes:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/1.png[/IMG]

So, on the above picture, I select:

> LAN\DHCP Server

Then, I get on the following picture:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/2.png[/IMG]

In there, I click on "Disable DHCP Server".
(my Internet connection is therefore gone - kaput!)

So, from the Menu, I then select:

> LAN\Routing - Static Routes

To get this:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/3.png[/IMG]

And in there, I click on the button named "Add", to get this:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/4.png[/IMG]

Then, I add the following info:

1. Under "Destination network address:", I type: 192.168.1.2
(the preferred Fixed IP of the 1rst Networked Ubuntu Desktop PC to connect to the Router)

2. Under "Subnet Mask:", I type: 255.255.255.0


I then click on the button named "Apply"...

...only to get this:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/5.png[/IMG]

What is wrong here?

What am I doing wrong?

Why can't I setup the Static IPs for my Desktop Ubuntu v6.06 Dapper PCs on the Router side?

What is this error:

> Unable to configure rooting. route: netmask and route address conflict.

How can I fix this?

Thanks.

P.S.> I have NOT yet worked on the Desktop PC's settings...
But it seems to me, that IF I can NOT fix/setup the Router's side (first), it turns non-worth-it to start working on the Desktop side's settings...

---

### Post by rbalfour on 2006-06-13
In the DHCP server section

Start address: 192.168.1.2
End address: 192.168.1.100

Then on your ubuntu PC.
Change from DHCP to static and use an ip address AFTER 192.168.1.100
Set the gateway and DNS to your router and subnet mask to 255.255.255.0

Static routes are for the router and not the client. This tells the route how to route differnet network.

ie. 10.19.73.0 routes to 192.168.1.1
Usally you don't use this unless you have more than one segment.

---

### Post by dvarsam on 2006-06-13
[QUOTE=rbalfour]In the DHCP server section:

Start address: 192.168.1.2
End address: 192.168.1.100[/quote]

Sorry, I did NOT get this...

You are suggesting that I leave the Router's side as is - set as DHCP?

Cause to set the above suggested settings is impossible when I select the option "Disable DHCP Server".

Please see what happens to the image below (when I "Disable DHCP Server"):

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/2b.png[/IMG]

These two fields are converted to "non-editable"...

So, in such a case, what do I do?

Should I leave the Router set as DHCP & only play with the Ubuntu Desktop's settings?

Will that work?


> Then on your ubuntu PC:

Change from DHCP to Static & use an IP address AFTER 192.168.1.100
Set the Gateway & DNS to your Router & subnet mask to 255.255.255.0

Static Routes are for the Router & NOT the Client.
This tells the Route how to Route different Network.

ie. 10.19.73.0 routes to 192.168.1.1
Usually you don't use this unless you have more than one segment.

So, the _Client's_ settings for:

1. Gateway = 255.255.255.0
2. DNS = 255.255.255.0
3. Subnet Mask = 255.255.255.0

They should _all_ be the same & equal to "255.255.255.0"?

And then you say that "Static Routes are for the Router & NOT the Client"...
So, to perform what I am suggesting is wrong...?

Sorry, I have lost it...

And then you say that "This tells the Route how to Route different Network."...
Which "this" are you reffering to?
The things you write below?

OR the things I performed & got me the "error" in the first place...?

Thanks.

P.S.> Sorry for being such "fruitcake" at this, but I do not seem to understand...
(I guess that if I _did_ know, then I wouldn't ask...):D

---

### Post by uzi09 on 2006-06-13
i've never really done this myself, but was thinking about it if i was planning on running any sort of a server.

please correct me if i'm wrong, but i thought you needed to request your ISP for a static IP address. and when they provide you with that info, you can disable DHCP as it says and tell the router what IP (the static one your ISP will provide) to use from now on.

---

### Post by dvarsam on 2006-06-13
[QUOTE=uzi09]i've never really done this myself, but was thinking about it if i was planning on running any sort of a server.

please correct me if i'm wrong, but i thought you needed to request your ISP for a static IP address. and when they provide you with that info, you can disable DHCP as it says and tell the router what IP (the static one your ISP will provide) to use from now on.[/QUOTE]

I have NO clue, about whether I need a Static IP over the Internet...

However, I am talking about setting Static IP for the "Intra" Network...
(the inside LAN!)

I always thought that an "inside" LAN could connect to the outside world (Internet) with a Dynapic IP (or even Static if you want), however, the Intranet (local LAN) _could_ also have Static (or Dynamic) addresses...?

I think that these 2 things are Independent from each other...!

Am I thinking right or wrong here?

Thanks.

P.S.> You see, I am trying to set some Shared Folders for my Local LAN, using NFS, but to do this successfully (to auto-mount from "fstab"), I need to Setup Fixed IPs for the Local LAN...!!!

---

### Post by uzi09 on 2006-06-13
oh, no sorry, i just didn't get that from your post. nevermind then...i'll look into it and let you know if i come up with something. it's also something i've been wondering, but never really came around to trying out.

EDIT: so like in windows, you would go to each computer, go to TCP/IP properties, and instead of "Obtain IP address automatically" you would specify the IP address.

---

### Post by JanVH on 2006-06-13
I also have a USR-router and under 'dhcp' I have a possibility to map a 'static' ip-address to a MAC-address. It's called 'fixed mapping'...

I don't if this is exactly what your looking for, but it works in my situation... Every computer always gets the same IP, and it's very easy to configure...

---

### Post by uzi09 on 2006-06-13
hmm, i found this:
> 
Changing Your IP Address

If you wanted, you could give this eth0 interface an IP address using the ifconfig command.

 

[root@bigboy tmp]# ifconfig eth0 10.0.0.1 netmask 255.255.255.0 up

 

The "up" at the end of the command activates the interface. To make this permanent each time you boot up you'll have to add this command in your /etc/rc.local file which is run at the end of every reboot.

Fedora Linux also makes life a little easier with interface configuration files located in the /etc/sysconfig/network-scripts directory. Interface eth0 has a file called ifcfg-eth0, eth1 uses ifcfg-eth1, and so on. You can place your IP address information in these files, which are then used to auto-configure your NICs when Linux boots. See Figure 3-1 for two samples of interface eth0. One assumes the interface has a fixed IP address, and the other assumes it requires an IP address assignment using DHCP.

source: [http://www.siliconvalleyccie.com/linux-hn/network-linux.htm](http://www.siliconvalleyccie.com/linux-hn/network-linux.htm)

---

### Post by dvarsam on 2006-06-13
Dear "JanVH",

Thank you for your reply!

> I also have a USR-router and under 'dhcp' I have a possibility to map a 'static' ip-address to a MAC-address.
It's called 'fixed mapping'...

Can you tell me where exactly is this located?

On your US-Robotics Menu, where do you go _exactly_?

Can you provide a rough idea on your steps you take to setup Fixed IP LAN connections?

> I don't know if this is exactly what your looking for, but it works in my situation... Every computer always gets the same IP, and it's very easy to configure...

YES, this is what I am looking for!
I do NOT mind if the Fixed LAN IP's are derived from MAC addresses or NOT...
I am just looking for a method - how to do it...!
(I have located the MAC address of my NIC card, but there is NO button saying: "connect fixed IP to MAC address"...)

Thanks.

---

### Post by dvarsam on 2006-06-13
Dear "uzi09",

Thanks for your reply!

> ...It's also something i've been wondering, but never really came around to trying out...

EDIT: so like in Windows, you would go to each computer, go to TCP/IP properties, and instead of "Obtain IP address automatically" you would specify the IP address.

Yes, but the difference is that you are suggesting a Method on how to work on the Ubuntu PCs...

Don't I first have to find how to Setup the Router?

You have also provided the following link:

[http://www.siliconvalleyccie.com/lin...work-linux.htm](http://www.siliconvalleyccie.com/lin...work-linux.htm)

Again, the above link does _NOT_ talk (at all) about setting up the Router...?

Before I even move to setting-up the Desktop PC's settings, don't I have to find a way to setup Router's settings first?

Thanks.

---

### Post by JanVH on 2006-06-13
[QUOTE=dvarsam]Dear "JanVH",

Thank you for your reply!



Can you tell me where exactly is this located?

On your US-Robotics Menu, where do you go _exactly_?

Can you provide a rough idea on your steps you take to setup Fixed IP LAN connections?



YES, this is what I am looking for!
I do NOT mind if the Fixed LAN IP's are derived from MAC addresses or NOT...
I am just looking for a method - how to do it...!
(I have located the MAC address of my NIC card, but there is NO button saying: "connect fixed IP to MAC address"...)

Thanks.[/QUOTE]

After entering the password, it's Basic Settings -> DHCP Server -> Fixed Mapping.

But I have to add that my web-interface does entirely look different than yours...

---

### Post by dvarsam on 2006-06-13
[QUOTE=JanVH]After entering the password, it's Basic Settings -> DHCP Server -> Fixed Mapping.

But I have to add that my web-interface does entirely look different than yours...[/QUOTE]

YES, I can NOT find _any_ options like the ones you have:

> Basic Settings -> DHCP Server -> Fixed Mapping

The only thing close to "Fixed Mapping" (that you have), seems to be my "LAN - Static Routes"...

I can NOT put it to work man...

Any ideas?

Thanks.

---

