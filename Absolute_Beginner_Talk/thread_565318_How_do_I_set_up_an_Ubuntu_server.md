---
title: "How do I set up an Ubuntu server?"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Bob_12 on 2007-10-02
I would like it to be a machine that has other Ubuntu computers auto back up data on the computer over a LAN and another computer auto backup over the internet to it. I know thats a lot to ask but I'm very new to Ubuntu! Thank you so much!

---

### Post by adza on 2007-10-02
Hey there, for server setup and installation, follow this how-to... it got my SUN Ultra 60 up and running no probs.. you may want to skip the mailserver setups and stuff just to do the backups, but hey.. if you're going to take the time to build the server, why not host your own mail and website? 

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

good luck!!

---

### Post by HermanAB on 2007-10-02
Any Ubuntu machine can do what you want to do using ssh and rsync, or FTP.

Note that a 'server' install is headless and is probably not what you want, since a home user wants to use a screen and keyboard plugged into the machine.  Server installs are for datacentres, where the machines don't have screens and keyboards, since it would be a waste of money.

Have a look at these guides for some ideas: 
[http://www.aeronetworks.ca/rsync-ssh-howto.html](http://www.aeronetworks.ca/rsync-ssh-howto.html)
[http://www.aeronetworks.ca/windows-backup.html](http://www.aeronetworks.ca/windows-backup.html)

Nowadays, I prefer to isntall Cygwin with OpenSSL on WIndows and then use rsync over ssh same as with Linux machines, since it is very reliable.

Cheers,

H.

---

