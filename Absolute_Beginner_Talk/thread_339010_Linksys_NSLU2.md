---
title: "Linksys NSLU2"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Iarwain ben-adar on 2007-01-15
Hiya people,

Got a question for you:
How can i access/install my NSLU2 via Ubuntu?

Because the Installation CD doesn't want to install the Web Interface :? (on windows that is)


Iarwain

---

### Post by Iarwain ben-adar on 2007-01-16
*bump*


Iarwain

---

### Post by Iarwain ben-adar on 2007-01-16
doesn't anybody know something about this?


Iarwain

---

### Post by mjblane on 2007-01-18
try a browser, default NSLU2 IP is 192.168.1.77, if your hub/router is assigning an address, you'll need to access the hub to find the correct address for the NSLU2

Good Luck

---

### Post by Iarwain ben-adar on 2007-01-20
Hiya,
i got it already working now,
just had to enter all info the CD was asking :?


Iarwain

---

### Post by HellRat on 2007-03-29
I'm interested in purchasing a NSLU2 and have some questions:

Does it work well with ubuntu?

Do I have to have a windows installation to configure it (initially)?

Anyone tried to install stuff from [www.nslu2-linux.org](www.nslu2-linux.org), how did that work out? 

If possible, I would like to use it both for storage and as a printserver for my Brother laser printer USB (with ubuntu ofc), anyone got that working?

---

### Post by Iarwain ben-adar on 2007-03-30
Hi there,

It works perfectly (but you do need a windows installation to get to the NSLU)

I have a debian running on it, together with ssh and nfs and apache. Runs very nicely :D

I can't help with the printer, as i don't have one...


Iarwain

---

### Post by HellRat on 2007-03-30
Need windows huh.. is that for initial configuration or will I need it even when I've installed debian on it?

If I reallyreally need windows, will it work through a VM-installation?

---

### Post by Iarwain ben-adar on 2007-03-30
Well, it could work via wine.. (you need to use an app to upgrade your NSLU with debian)

> Regardless of which image you intend to use, you should configure your network settings (IP address, DNS, hostname) using the web interface before flashing the debian-installer image in case you do not want to use DHCP. Debian's installer will use those settings to bring up the network. Also make sure that your hostname is valid (for example, a hostname must not contain the character _). [http://www.cyrius.com/debian/nslu2/install.html](http://www.cyrius.com/debian/nslu2/install.html)

I did it with another utility (i didn't know enough to get it to work an other way)
Can't seem to find the app now..

But have a read on the site, and you're bound to find some answers.

As for using it: it is a seperate computer serving (files/site/...)

So as soon as it is set up, you can access it with whatever you like :D


Iarwain

---

### Post by HellRat on 2007-03-30
Great! Thanks a bunch, I am to remove my win-partition as soon as I fixed this storage-problem. So now I guess I just keep it until the nslu2 is working.

Thx!

---

### Post by Iarwain ben-adar on 2007-03-30
Glad to have been of some help xD


Iarwain

---

### Post by HellRat on 2007-04-10
Well, my slug is working as expected with the standard firmware. Now I really want to do the debian install but I'm not sure I know my way around linux well enough to configure it to do the things I want it to.

So, since the nslu2-linux.org page doesn't say much about Debian except for how to install it (have I missed something?) I wonder if its an easy task to "share" the drive on the network once I have a working Debian installation. I also wonder how I set it up as a ftp-server. Later on I plan to install my printer on it and then share it on my home-network.

Is there a good newb-oriented webpage for stuff like this? Can give me a hint?

Thanks!

---

### Post by Iarwain ben-adar on 2007-04-11
It all depends:
To share once you have your Debian installed, you can go Samba or NFS (or both)
Samba = windows client
nfs = linux client

To see how you have to set those services up, search the forums ;)

Idem for ftp :D

I don't know anything about printers, so i can't help about that..


Iarwain

---

