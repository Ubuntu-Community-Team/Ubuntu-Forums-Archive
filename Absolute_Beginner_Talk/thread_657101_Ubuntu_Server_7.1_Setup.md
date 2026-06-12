---
title: "Ubuntu Server 7.1 Setup"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by WNxCryptic on 2008-01-03
I'm a long-time web developer and I've finally gotten around to setting up a local development server for testing server side languages without needing an actual online server. Unfortunately, I want to do everything the "right" way...which means no GUI, and my terminal knowledge is..well, nothing.

Here's what I want to accomplish:

1. Setup apache and possibly an FTP
2. Allow for remote desktop from a windows computer onto the linux server
3. Obtain the ip address of the linux box from within the console.

---

### Post by stump138 on 2008-01-03
Well there are several ways you can go:)

I'll try and take in order:)

You can set up apache right off of the install disk iirc.  If not you can install apache from terminal with:

```
sudo apt-get install apache2
```

For your ftp program you can use proftpd there is a good tutorial [here]("http://ubuntuforums.org/showthread.php?t=79588")

For remote access you'll need to SSH into the box.  You can find information [here]("https://help.ubuntu.com/community/SSHHowto")

To get your ip address from the terminal you can type
```
ifconfig
```

that will display your information.  If you need to set your IP static, there is a way to do that as well :)  iirc /etc/network/interfaces

If you plan on not installing any GUI you'll need to learn nano or vi  to edit files. You can find information all over on those

---

### Post by Cypher on 2008-01-03
After installing Ubuntu Server..you can install Apache with the following
```

sudo apt-get install apache2

```
Look in /etc/apache2/conf.d for the configuration files. There are numerous websites online that describe how to configure Apache so I won't bother with that here.

Install FTP with
```

sudo apt-get install wu-ftpd

```
You should now be able to start/stop it from System->Administration->Services

Since you are not going to be running a GUI on the server, remote desktop is not really what you want. Rather, install the SSH server (openssh-server) and use PuTTY on Windows to connect to the shell.

To obtain the IP address of the Linux server on it's own console, type "ifconfig"..

---

### Post by RavUn on 2008-01-03
[http://www.linuxhomenetworking.com/#Linux%20Main](http://www.linuxhomenetworking.com/#Linux%20Main)

This helped me a lot when I was experimenting.

---

### Post by hyper_ch on 2008-01-03
here you can have a total ISP setup.

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

### Post by WNxCryptic on 2008-01-03
Ok, I think I've got some understanding of what all is going on. I installed ubuntu-desktop last night because I was thinking that I wanted to use a GUI, but I've since decided to do everything via console...Thus all my nooby questions ;)

Moving onward! Once I have apache setup, how would I access it on another computer from within that same network (simply [http://ip.address.ofcomputer.here/](http://ip.address.ofcomputer.here/) ??)

Also, I'm mainly working with PHP and ASP.net (and maybe a litle mySQL), can someone point me to a noob friendly guide for setting those up using only the console?

---

### Post by hyper_ch on 2008-01-03
The link I posted above will give you steps to install mysql, apache2, php5 and phpmyadmin.

Basically you can reach them with the IP. Or if you want to have it more confortable, give that other computer a static IP, modify your /etc/hosts and enter something like this:

```

168.0.0.5 REMOTECOMPUTER

```
168.0.0.5 --> that's the IP of the other computer
REMOTECOMPUTER --> enter a name for it.... e.g. myserver  or  [www.testserver.com](www.testserver.com) or ....

Then you can just enter that in your browser and it will connect to it on the assigned IP... if you do want to do website development it's better to use the "real" domain name ;)

---

### Post by WNxCryptic on 2008-01-03
> **hyper_ch said:**
> Then you can just enter that in your browser and it will connect to it on the assigned IP... if you do want to do website development it's better to use the "real" domain name ;)

What is the "real" domain name?

And can I still set that ip address to something like 165.0.0.8 even if I'm using a router w/ DHCP and whatnot? Would that prevent that computer from having actual internet access?

---

### Post by stump138 on 2008-01-03
Giving your computer a "static" ip address will only be a problem if there is another computer on your subnet using the same address.  Your internet access would only be affected if you change the default gateway.  So long story short, setting a static IP address is generally a non-issue and shouldn't cause problems as long as you are careful about your addressing (hint: give it an address that is higher up in the subnet.  If the router is at 192.168.0.1 give your server an address like 192.168.0.34 or something:))

If your apache setup is proper, then you can access the hosted website exactly as above:

[http://ip.address.of.server.here/](http://ip.address.of.server.here/)

What hyper-ch is referring to is editing your hosts file, which simply overrides/acts like DNS (short version ot it).  If you are just setting up the server, using the IP address is fine to get started and settle in.

---

### Post by WNxCryptic on 2008-01-03
Where can I find the hosts file and what would I put in in place of a DNS?

---

### Post by stump138 on 2008-01-03
the hosts file is located at /etc/hosts

you can open it with nano or vi:

```
sudo nano /etc/hosts
```

what you would do then is add in a line for your server and give it a name. example: if your server was at address 192.168.0.34 and you wanted to call it "webserver" you would make an entry that looks like this to the file:

```
192.168.0.34  webserver
```

then you could open a web browser and access your web server by tying
[http://webserver](http://webserver)

or

[http://192.168.0.34](http://192.168.0.34)

---

### Post by WNxCryptic on 2008-01-03
I've tried following the guide you've given me, hyper_ch ([http://www.howtoforge.com/perfect_server_ubuntu7.10_p3](http://www.howtoforge.com/perfect_server_ubuntu7.10_p3))

But when I try to set a static IP address, I can no longer SSH into the server (even with the new 192.168.0.100) address.

---

### Post by WNxCryptic on 2008-01-03
Furthermore, I've installed SAMBA and SWAT, and I can't seem to get either working (can't FTP into my server and access to swat via serverip:901 returns address not found).

EDIT: I can access SWAT, but FTP still does not work.

2nd EDIT: When I access swat, if I click on "SWAT" under "Administrative Utilities" it brings me to a 404 page cannot be found...It seems I am missing some of the swat files, but I installed it using:

```
sudo apt-get install swat
```

The status page of swat reports:

Version: 3.0.26a
smbd: running
nmbd: running
winbindd: not running

Active Connections, Active Shares, and Open Files are all empty.

Current Config:

```
# Samba config file created using SWAT
# from 192.168.1.100 (192.168.1.100)
# Date: 2008/01/03 21:00:11

[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Share]
	valid users = culture
	admin users = culture
	read only = No
	available = No
```

---

### Post by WNxCryptic on 2008-01-04
EDIT: Nevermind..I'm going with vsftp.

---

