---
title: "internet connection at home is fine.  Ubuntu can't find net at college library."
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by flash722 on 2006-07-10
Hi folks.  Been running ubuntu now for about a month.  The learning curve is gradually coming along.  Here's my issue.

I run ubunutu on my Dell c600 notebook and also run a windoze 2000 machine on my LAN.  Ubuntu found my cable modem upon installation with no problem.  However, I'm a grad-student and when I take the notebook to the library on campus, I cannot pick up the network.  I could do it with XP simply by resetting the internet connection and it picked it up without issue.  Reset it again at home.  This also worked with a Mac running OSX.

How do I do the same in Ubuntu?  Don't seem to find it in the internet connection settings and I'm probably not well-versed enough in netmworking terms to search for it properly in the help files.  I'm thinking this has to do with dynamic versus static IP's?

Thanks!

Adam

---

### Post by Paerez on 2006-07-10
do you use network manager? It is very similar to windows's wireless networking utility, except it will manage both the wireless and wired networks you connect to. Grab it from synaptic (I think its called "network-manager") then you just have to log out and log back in and it should be in your notification area (taskbar).

edit: thanks to rowanparker pointing out that its "network-manager"

---

### Post by rowanparker on 2006-07-10
Just to point out: It's "network-manager" not "networkmanager".

---

### Post by steve.horsley on 2006-07-10
I guess you are using DHCP - the dynamig host configuration protocol that tells PCs what IP address etc. to use. I would have thought the college LAN was too, so I have no immediate idea what could be wrong. Once connected to the college LAN, try these commands and capture the output to post here. Note that I use "eth0" in my example, but your ethernet interface name might just be different. The first ifconfig will tell you what name to use in the dhclient command.
> 
ifconfig
sudo dhclient eth0
ifconfig
route

---

### Post by BigDave708 on 2006-07-10
> **flash722 said:**
> I'm thinking this has to do with dynamic versus static IP's?

Does your network (you're plugged into a router, I presume) automatically assign computers IP addresses via DHCP? I know that when I used Windows and I connected it to my router, it would always be very fussy about being told what IP address it should use on the network. Not sure if it is the same on Ubuntu however . . .

(Does anybody know where I can change whether my computer works via DHCP or not in Ubuntu? - I manually assign my computers IP addresses now every time I install Ubuntu.)

EDIT: It appears that Steve has already mentioned the DHCP thing above while I was typing ](*,).

---

### Post by jenred on 2006-07-10
One more step to make network-manager work:

Make sure you disable all of your interfaces via System | Networking

Highlight each interface and select Properties and then remove the check from the box that says "enable this connection."

Then run network-manager.  The latest version is working really well.  I've been switching networks with very little hassle.

---

### Post by flash722 on 2006-07-10
Thanks for the suggestions everybody!  It looks as though the simplest first step is to try network-manager.  I'll let ya' know how it goes!

Adam


> **flash722 said:**
> Hi folks.  Been running ubuntu now for about a month.  The learning curve is gradually coming along.  Here's my issue.

I run ubunutu on my Dell c600 notebook and also run a windoze 2000 machine on my LAN.  Ubuntu found my cable modem upon installation with no problem.  However, I'm a grad-student and when I take the notebook to the library on campus, I cannot pick up the network.  I could do it with XP simply by resetting the internet connection and it picked it up without issue.  Reset it again at home.  This also worked with a Mac running OSX.

How do I do the same in Ubuntu?  Don't seem to find it in the internet connection settings and I'm probably not well-versed enough in netmworking terms to search for it properly in the help files.  I'm thinking this has to do with dynamic versus static IP's?

Thanks!

Adam

---

### Post by flash722 on 2006-07-12
Thanks everybody!  Network manager worked like a charm.  I'm typing this from the library!  :)  Now on to getting my Palm to work properly..  


Adam

---

