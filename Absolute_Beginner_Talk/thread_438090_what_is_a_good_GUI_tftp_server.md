---
title: "what is a good GUI tftp server?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Rush_898 on 2007-05-09
I found a package called tftpd-hpa in synaptic and then gproftp, which I can't figure out if it does tftp or not, but I can't find a good simple GUI program for tftp.  I tried the almighty google to no avail, does anyone have a suggestion?


Thanks a lot.

---

### Post by Kobalt on 2007-05-09
There is a simple debian package called tftp, I don't know if that's what you're looking for... [http://packages.debian.org/stable/net/tftp](http://packages.debian.org/stable/net/tftp)

---

### Post by SyL on 2007-05-09
try gftp.
It's really easy and stable.


EDIT: gftp is a ftp client not a server. Are you looking for a client or you want to run your own ftp server?

---

### Post by Rush_898 on 2007-05-09
I need a tftp server.  I looked at tftpd and I couldn't figure out how to use it.  Maybe it is so simple that it is confusing me, but I couldn't find a good tutorial on the net.  I looked through all the files and became more confused.

---

### Post by cjsteele on 2008-01-28
to the better of my knowledge there is no such beast... you basically have to:

** install tftpd via `apt-get install tftpd`
** configure the tftp directory in /etc/inetd.conf on the line that starts "tftp"
** start openbsd-inetd via `/etc/init.d/openbsd-inet start` as root.

I don't advise you leave tftpd running as it is trivially abused.

-C

---

### Post by Dr Small on 2008-01-28
You could install proftpd, and then gproftpd, for the graphical interface to control it.

Dr Small

---

### Post by AzureCerulean on 2008-04-17
Are you looking for a Tftp server or a FTP server?

these are 2 different things.

Trivial File Transfer Protocol (TFTP) is a very simple file transfer protocol, with the functionality of a very basic form of FTP; it was first defined in 1980.

File Transfer Protocol (FTP) (Port 21) is a network protocol used to transfer data from one computer to another through a network, such as over the Internet.

1) Know what you are asking 
2) Know what you are answering

---

### Post by shazbut on 2008-04-17
I assume the OP wants a **tftp** frontend similar to the free solarwinds tftp program many people use under windows.  Probably for PXE booting or transferring files to/from cisco gear.  Last time i looked I wasn't able to find a gui for tftp in linux, I doubt anyone's bothered to write one, since it's a bit of a niche within a niche.  I did manage to get the daemon working from the command line, I probably just googled tftpd ubuntu and followed a guide like this one:
[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/]("http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/")

---

### Post by scorp123 on 2008-04-17
> **SyL said:**
> try gftp. It's really easy and stable. EDIT: gftp is a ftp client not a server. Are you looking for a client or you want to run your own ftp server? > **Dr Small said:**
> You could install proftpd, and then gproftpd, for the graphical interface to control it.  FTP and TFTP are not the same protocols. Someone further up already mentioned that. FTP (for which "gftp" is a client) is used to transfer files between e.g. a server and a client PC. There is username + password authentication. TFTP however is a downright simple and stupid protocol without any authentication and you'd only use it to transfer boot images from a TFTP-server to e.g. a router that needs TFTP or else it cannot boot (most routers don't come with e.g. floppy disk drives so they need to get their boot blocks by other means).

---

### Post by jaburr on 2008-05-07
I've been using this program for the past year with good luck.

[http://code.google.com/p/tftpgui/](http://code.google.com/p/tftpgui/)

I mainly use it for uploading images to Cisco boxes.  Nice too because it doesn't stay running -- you invoke it & turn it off as-needed.

JB

---

### Post by scubanator87 on 2008-05-07
Well if you are trying to do FTP and have a gui front end there is always webmin. 

However, FTP is server oriented software ergo no gui interface naitively on Linux since it is not necessary for a server. Same is true for TFTP. 

Also TFTP server would not really be for sending files to a cisco box that would be a tftp client since the server side is running on the cisco box. 

What webmin will do is it will give you a web based administrative interface for alot of different server services like FTP, SSH, MySQL etc. 

Another alternative is ISPConfig. 

Stay away from gproftp because like most "gadmintools" it may add a gui but it tends to require more input and be more confusing than just simble config file editing. 

[http://www.webmin.com/](http://www.webmin.com/)

[http://www.ispconfig.org/](http://www.ispconfig.org/)


My 2-bits any way.

---

### Post by shazbut on 2008-05-07
Thanks jaburr, that's what we were looking for.  Had to do this to get it working right first:
sudo apt-get install python-tk

PS: Anyone know how to make a panel launcher run as super-user?  I've tried putting gksudo, gksu, sudo in front of the following command with no success:
sh -c "cd /home/shazbut/Desktop/tftpgui_1_1/ && python tftpgui.py"
Have to run it as super user to get it working on the normal tftp port.

---

