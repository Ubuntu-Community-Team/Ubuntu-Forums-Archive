---
title: "Desktop or Server?"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by IrDA Ranger on 2007-01-25
Hello all; my first post and very new to Linux.  Mostly Windows, some Mac experience.

A quick question before I start doing some serious reading on how this all works.  I am thinking of buying a cheap, off-lease computer (something like [this]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2717587&Sku=J156-4284")) to use as a home server.  Do I need to use the Ubuntu Server edition to do that, or can I use the Desktop version?  I'm only asking because I think Desktop would have a gentler learning curve.

As a matter of further guidance (if it matters), I'm primarily interested in using this server as:
[LIST]
[*]Router
[*]File server / backup & archive utility
[*]Bittorrent client
[*]VPN gateway
[*]Printer sharer
[/LIST]
All thoughts and advice appreciated.  Thanks!

---

### Post by taurus on 2007-01-25
Install the desktop version and then install whatever else you need to run it as a server.  That way, you would have a nice GUI (Gnome) to configure everything unless you want to do that from a terminal.

---

### Post by compiledkernel on 2007-01-25
Id recommend installing a lighter DE for a server (fluxbuntu or xubuntu -- [http://fluxbuntu.org/](http://fluxbuntu.org/) and [http://www.xubuntu.org/](http://www.xubuntu.org/) respectively). That way resources are set use to minimal, but allows for a graphical interface for completing tasks.

---

### Post by kebes on 2007-01-25
If you're new to Linux it's easier to do a Desktop install and then add server packages. If you do a server install, then you start with a commandline system that can be very hard to use if you're not comfortable with the Linux command-line. (It is possible to install the desktop software into the Server setup, but it's easier to start with a Desktop system.)

The potential hardware you pointed out should be more than enough to run Gnome properly, so I wouldn't worry about that.

All of the functionality you mentioned can be installed into a Linux server without problems. One suggestion: if you're creating a server that will be running bit-torrent, I would suggest using "torrentflux" as the bit-torrent client. This client is designed to be used remotely. It creates a nice web interface that you can log into (from anywhere in the world, in fact!) and start/stop/manage your bit-torrent transfers. Very convenient.


Good luck, and feel free to post any other questions you may have.

---

### Post by az on 2007-01-25
You would be able to run the desktop version and all those services on a much less powerful machine and still get excellent results.

The desktop does not really give you that many more tools to use for configuring the services you describe - you will still need to use the command line to install and configure them reliably.  

However, the reason there are not so many GUI tools for server functionality is that the command line can be very very efficient and powerful.

---

### Post by hyper_ch on 2007-01-25
Just go ahead with desktop install... for email/web/ftp server you can then look at this howto:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

---

### Post by IrDA Ranger on 2007-01-25
Great, thanks for your quick replies!  I don't mind learning to use the command-line every now and then, but I'd really prefer to have the GUI when possible, just as a matter of ease-of-use and getting started.

Thanks for your help, and suggestions.

And Azz, nice avatar. :)

---

