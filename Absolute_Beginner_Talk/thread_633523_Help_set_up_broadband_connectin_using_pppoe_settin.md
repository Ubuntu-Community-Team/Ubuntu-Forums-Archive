---
title: "Help set up broadband connectin using pppoe settings"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by PogMoThoin on 2007-12-06
Hi all,

While I'm not long using Ubuntu, getting there, I feel i'm still a noob so i'm posting here. Mods move it if you have any objections.

I've got a main pc (dual boot Vista & Gutsy), laptop (Gutsy) & now I've just setup an old Dell Pentium 4 as a server(Ubuntu Server). I'll start @ the begining:

I installed Ubuntu as dual boot my main pc, but since i couldn't connect to my broadband as its pppoe i just setup the pppoe settings on a four port wireless router as it was easier. I have no idea how to set it up.

Now i've built my server with 2 network adapters, Eth0 has a static ip of 192.168.1.2 to allow it connect to the router(192.168.1.1), did this while installing to allow me get updates & packages, & eth1 has 192.168.10.1 which i will use for my lan (i used vim to add eth1 to /etc/)network/interfaces). I now want to be able to move the router & configure the server for pppoe to connect to my broadband & put the router after the server on my internal network.

Anyone know how i modify eth0 in /etc/network/interfaces with dchp & pppoe settings?

Thanks in advance

Pog

---

### Post by Swmmrman on 2007-12-06
A few questions.  Who is your ISP and what type of router was this?

---

### Post by PogMoThoin on 2007-12-06
As i live in Ireland, my provider is a small wireless provider. They only give information on how to use windows to connect & use dynamic pppoe & dns settings. They give very little settings, just username & password & tell you to use dynamic. The router is a dlink 4 port wireless router.

---

### Post by PogMoThoin on 2007-12-06
I found [this]("https://help.ubuntu.com/7.10/internet/C/modems-adsl-pppoe.html") but don't know what to do on the server. I need it to automatically connect & there's a few things i dont understand, all i have is my username & password.

---

### Post by stchman on 2007-12-06
> **PogMoThoin said:**
> Hi all,

While I'm not long using Ubuntu, getting there, I feel i'm still a noob so i'm posting here. Mods move it if you have any objections.

I've got a main pc (dual boot Vista & Gutsy), laptop (Gutsy) & now I've just setup an old Dell Pentium 4 as a server(Ubuntu Server). I'll start @ the begining:

I installed Ubuntu as dual boot my main pc, but since i couldn't connect to my broadband as its pppoe i just setup the pppoe settings on a four port wireless router as it was easier. I have no idea how to set it up.

Now i've built my server with 2 network adapters, Eth0 has a static ip of 192.168.1.2 to allow it connect to the router(192.168.1.1), did this while installing to allow me get updates & packages, & eth1 has 192.168.10.1 which i will use for my lan (i used vim to add eth1 to /etc/)network/interfaces). I now want to be able to move the router & configure the server for pppoe to connect to my broadband & put the router after the server on my internal network.

Anyone know how i modify eth0 in /etc/network/interfaces with dchp & pppoe settings?

Thanks in advance

Pog

In the router you have the option of doing PPoE.  Most routers default to DHCP.  Select PPoE and then let the router store your username and password.  Simple.

---

### Post by PogMoThoin on 2007-12-06
> **stchman said:**
> In the router you have the option of doing PPoE.  Most routers default to DHCP.  Select PPoE and then let the router store your username and password.  Simple.

Hey, u didn't read properly, thats what i did originally, now i've got a server setup i want to connect that directly to my broadband. I need to know how to setup pppoe on the server using cli only as its ubuntu server.

---

### Post by PogMoThoin on 2007-12-06
will > sudo pppoeconf work on ubuntu server, i'll need to set /etc/network/interfaces from static to dchp 1st, how do i do that? what will the lines for eth0 look like? I can easily modify with vim, but what do i change it to?

---

### Post by PogMoThoin on 2007-12-07
ok, update, i figured it. sudo pppoeconf works on ubuntu server :)

now i've ran in2 a problem, i want to install shorewall, but everytime i try it asks for the cd, but my cdrom obviously isn't mounted.its not listed when use command "mount". How can i find the name of the device to mount it as i cant use gparted, or can i? i need to mount the cdrom before i can install shorewall

---

### Post by PogMoThoin on 2007-12-07
Used command "cat /etc/fstab" and it shows that i've got a line for cdrom
> /dev/scd0          /media/cd0    udf,iso9660 user, no auto , exec  0

this shows the cd is in the tray,but it cant find it...help

---

