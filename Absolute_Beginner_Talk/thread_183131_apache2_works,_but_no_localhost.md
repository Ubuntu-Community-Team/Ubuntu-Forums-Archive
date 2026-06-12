---
title: "apache2 works, but no localhost??"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by F Cocquyt on 2006-05-27
Hi group,

I've recently installed the apache2 http server following the wiki page. I can start and stop the server using /etc/init.d/apache2 start or stop (so I'm presuming the installation went right) but I can not see the localhost page on my browser. I am getting a timeout error. I don't have a firewall installed. Could someone help me or give me a hint on how to make things work??

Thanks in advance
Frederik

---

### Post by ifokkema on 2006-05-27
[QUOTE=F Cocquyt]I've recently installed the apache2 http server following the wiki page. I can start and stop the server using /etc/init.d/apache2 start or stop (so I'm presuming the installation went right) but I can not see the localhost page on my browser. I am getting a timeout error. I don't have a firewall installed. Could someone help me or give me a hint on how to make things work??[/QUOTE]

Hi,

Could you check if apache runs by running:
```
ps -ef |grep apache
```

Also, check the apache log files if you might have gotten a warning of some sort.

Ivo

---

### Post by F Cocquyt on 2006-05-27
[QUOTE=ifokkema]Hi,

Could you check if apache runs by running:
```
ps -ef |grep apache
```
[/QUOTE]

here you are:

[ATTACH]10155[/ATTACH]


> 
Also, check the apache log files if you might have gotten a warning of some sort.


I don't see an error in my error log, only notices.:

[Sat May 27 19:10:25 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 configured -- resuming normal operations
[Sat May 27 19:18:29 2006] [notice] caught SIGTERM, shutting down

and every entry is the same (except time and date of course).

---

### Post by mlind on 2006-05-27
what about /var/log/apache2/error.log ?

how does your /etc/hosts look like?

/edit
sorry, I meant /var/log/messages

---

### Post by skippy81 on 2006-05-27
This might help in diagnosing the problem.

> sudo apt-get install nmap

> sudo nmap 127.0.0.1

Post the output here.

If port 80 / http doesnt show up then you are either firewalled, or apache is simply not running.

If port 80 is shown, then I would guess you just need to tweak some config files.

You could try installing firestarter, just incase your kernel has iptables enabled and is somehow blocking port 80.

---

### Post by F Cocquyt on 2006-05-27
[QUOTE=mlind]what about /var/log/apache2/error.log ?

how does your /etc/hosts look like?
[/QUOTE]

127.0.0.1 localhost.Laptop Laptop localhost

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

> 
/edit
sorry, I meant /var/log/messages

The file is quite big so can you tell me what I should be looking for?

---

### Post by adamkane on 2006-05-27
Hassle-free LAMP (Linux/Apache/MySQL/PHP) installation:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

---

### Post by F Cocquyt on 2006-05-28
[QUOTE=adamkane]Hassle-free LAMP (Linux/Apache/MySQL/PHP) installation:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```[/QUOTE]
[LIST]
[/LIST]

Thanks for the advice but I've tried that already, same effect.

---

### Post by ifokkema on 2006-05-28
Nmap (post #5) is a good idea, since it seems Apache is running properly but it is apparently not being reached.

F Cocquyt, could you post nmap's output (run as described in post #5) here?

---

### Post by F Cocquyt on 2006-05-28
The output of Nmap is the following:

Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-05-28 17:32 CEST
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 2.060 seconds

how does this rhyme with the output of ps -ef|grep apache (see post#3) ??

---

### Post by ifokkema on 2006-05-28
[QUOTE=F Cocquyt]The output of Nmap is the following:

Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-05-28 17:32 CEST
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 2.060 seconds

how does this rhyme with the output of ps -ef|grep apache (see post#3) ??[/QUOTE]

Wow... nmap on 127.0.0.1 sends THAT as a reply? This means that your computer can't even ping itself... even if you have a firewall installed, it's as strict as it can get.

Try this: 
```
sudo nmap -P0 127.0.0.1
```

This may take some time to run, but it does a very thorough scan of your ports. It seems that a firewall is blocking everything coming to your computer, even when the connection is coming from the computer itself.

---

### Post by mlind on 2006-05-28
I reckon it can't be caused by firestarter, but some router or NAT ?

If you install firestarter, and apply just leave it with default configuration, you make
sure that iptables is configured okay for apache httpd.

---

### Post by F Cocquyt on 2006-06-03
I finally found it. My local loopback doesn't start at bootup. If I enter 
```
sudo ifconfig lo up
``` in a terminal, I can reach apache. 
can anyone tell me how to get my local loopback running on startup?

---

### Post by mlind on 2006-06-03
[QUOTE=F Cocquyt]I finally found it. My local loopback doesn't start at bootup. If I enter 
```
sudo ifconfig lo up
``` in a terminal, I can reach apache. 
can anyone tell me how to get my local loopback running on startup?[/QUOTE]

does you /etc/network/interfaces contain
```

# The loopback network interface
auto lo
iface lo inet loopback

```

---

### Post by F Cocquyt on 2006-06-04
[QUOTE=mlind]does you /etc/network/interfaces contain
```

# The loopback network interface
auto lo
iface lo inet loopback

```[/QUOTE]

there is a 
"iface lo inet loopback", a "auto ath0" and a "auto eth0" but no "auto lo". Do I simply add it anywhere in the file?

---

### Post by mlind on 2006-06-04
[QUOTE=F Cocquyt]there is a 
"iface lo inet loopback", a "auto ath0" and a "auto eth0" but no "auto lo". Do I simply add it anywhere in the file?[/QUOTE]

I'll post the contes of my unmodified /etc/network/interfaces file.
It was done by Dapper installer.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

After you've modified the file, do *sudo /etc/init.d/networking restart*

---

