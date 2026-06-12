---
title: "ADSL internet problem"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by measdg on 2006-07-27
Hi, I am a new Ubuntu user.

I am unable to access the internet in Ubuntu Linux at home.
It is a new install (from CD) onto my Dell Laptop. I have ADSL at home, which I normally access using a wireless router.

The network configuration tool seems to recognise both my ethernet card, and my wireless card. Using both the wireless and wired connections I have been able to access the routers internal setup through Firefox so it seems to be talking to the router properly. But I still am unable to access the internet using either the wired or wireless connections.

I have:
Dell Inspiron 9400 Laptop
Intel 3945ABG Wireless
Broadcom 440x 10/100 Ethernet Controller

Connecting to a D-link DSL-G604T Wireless ADSL Router.

Any tips on how to fix this problem, or on some relevant documentation to help?

---

### Post by MaximB on 2006-07-27
do you need to insert a password and a user name for your ISP ?
and do you need to go to the configuration of your ADSL ?
if so (I don't know much about wireless)
go to the terminal (I hope you know were it is :))
and copy/paste the command :
sudo pppoeconf
enter your ubuntu password and go to the configuration...

---

### Post by measdg on 2006-07-27
Hi,

The ADSL router does require a password/username but these are set up in the router configuration already (I am using the internet now through it on my PC). So my ADSL is set up properly already, it is just that Ubuntu doesnt seem to go onto the net through it.

I have tried the "sudo ppoeconf" command already (I have searched around a bit already in these forums) and that did not seem to work, it said that it could not detect either my eth0 (wireless connection) or eth1 (wired ethernet connection).

I use Linux/Unix alot at work, so I know a fair bit about how to work in these environments, but I am a complete newbie at setting it up myself from scratch.

---

### Post by measdg on 2006-07-27
Fixed it!!

The solution was contained in a few of the treads in the 'Networking' section of these Forums. I Imagine other people will be having this problem so I will paraphrase my solution here. I have linked the helpful threads.

It turns out my network/wireless/ADSL etc. was set up properly it was just that it was EXTREMELY slow. To fix it I did:

1) in a terminal I typed: host [www.google.com](www.google.com)
  This tries to get googles ip number, This returned a proper ip number so it told me I was connected.
 2) i then edited my /etc.modprobe.d/aliases file to disable ipv6
3) I then disabled the ipv6 setting in mozilla firefox.

Thois thread: [http://www.ubuntuforums.org/showthread.php?t=87798&highlight=about%3Aconfig](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=about%3Aconfig)

basically helped me the most.

---

