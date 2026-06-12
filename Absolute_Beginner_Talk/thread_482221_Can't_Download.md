---
title: "Can't Download"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by chrisbish on 2007-06-23
im a newb to ubuntu.
just installed it last night.
i booted ubuntu up this morning as played around on it for about 3 hours downloading software and sound codac.
everything was working until 5 mins later I  could'nt  download anything from the synaptic package manger, add/remove programs or Automatix.

can anyone help me?

---

### Post by Regel on 2007-06-23
Try to install something from the terminal.

Like
```
sudo apt-get install tropic-look
```
What's the output of that command?

---

### Post by chrisbish on 2007-06-23
It gave me:

> chris@chris-desktop:~$ sudo apt-get install tropic-look
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  tropic-gdm-theme tropic-session-splashes tropic-theme tropic-wallpapers
The following NEW packages will be installed
  tropic-gdm-theme tropic-look tropic-session-splashes tropic-theme
  tropic-wallpapers
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 1163kB of archives.
After unpacking 1614kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe tropic-gdm-theme 0.2-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe tropic-theme 0.2-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe tropic-session-splashes 0.2-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe tropic-wallpapers 0.2-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe tropic-look 0.2-0ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/t/tropic-look/tropic-gdm-theme_0.2-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/t/tropic-look/tropic-gdm-theme_0.2-0ubuntu1_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/t/tropic-look/tropic-theme_0.2-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/t/tropic-look/tropic-theme_0.2-0ubuntu1_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/t/tropic-look/tropic-session-splashes_0.2-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/t/tropic-look/tropic-session-splashes_0.2-0ubuntu1_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/t/tropic-look/tropic-wallpapers_0.2-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/t/tropic-look/tropic-wallpapers_0.2-0ubuntu1_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/t/tropic-look/tropic-look_0.2-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/t/tropic-look/tropic-look_0.2-0ubuntu1_all.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
chris@chris-desktop:~$ 


---

### Post by Regel on 2007-06-23
and what about
```
ping www.google.com
```

---

### Post by chrisbish on 2007-06-23
here you are:

> chris@chris-desktop:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.102.9.147) 56(84) bytes of data.
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=1 ttl=243 time=42.9 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=2 ttl=243 time=43.2 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=3 ttl=243 time=43.8 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=4 ttl=243 time=41.7 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=5 ttl=243 time=40.8 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=6 ttl=243 time=65.9 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=7 ttl=243 time=46.0 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=8 ttl=243 time=44.4 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=9 ttl=243 time=44.7 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=10 ttl=243 time=44.8 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=11 ttl=243 time=45.1 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=12 ttl=243 time=45.6 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=13 ttl=243 time=42.9 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=14 ttl=243 time=44.5 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=15 ttl=243 time=45.9 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=16 ttl=243 time=44.8 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=17 ttl=243 time=53.0 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=18 ttl=243 time=45.8 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=19 ttl=243 time=51.8 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=20 ttl=243 time=45.3 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=21 ttl=243 time=46.4 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=22 ttl=243 time=44.7 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=23 ttl=243 time=46.4 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=24 ttl=243 time=42.3 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=25 ttl=243 time=45.2 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=26 ttl=243 time=46.0 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=27 ttl=243 time=45.2 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=28 ttl=243 time=40.6 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=29 ttl=243 time=42.9 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=30 ttl=243 time=42.1 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=31 ttl=243 time=43.9 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=32 ttl=243 time=41.5 ms
64 bytes from lm-in-f147.google.com (66.102.9.147): icmp_seq=33 ttl=243 time=43.2 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
33 packets transmitted, 33 received, 0% packet loss, time 32012ms
rtt min/avg/max/mdev = 40.648/45.300/65.900/4.441 ms
chris@chris-desktop:~$ 


---

### Post by Regel on 2007-06-23
> 
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe tropic-gdm-theme 0.2-0ubuntu1
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

it tries to connect to your own pc, instead of the real server. That's odd.

You dont use any proxies, do you.

Edit: Maybe you shoud try to edit your /etc/apt/sources.list, and use different servers.

---

### Post by chrisbish on 2007-06-23
i know what the porbleme is now

it downloaded a proxie thing off of the downloads.

im going to see if i can find it and uninstall it

---

### Post by Regel on 2007-06-23
```
sudo dpkg-reconfigure anon-proxy
```
Some1 used that command to get rid of the proxy problem. I wonder if it works for you too.

---

### Post by chrisbish on 2007-06-23
i couldn't find it

i tryed the code
> chris@chris-desktop:~$ sudo dpkg-reconfigure anon-proxy
Password:
Stopping Anonymising Proxy Service: anon-proxy.
Stopping Anonymising Proxy Service: anon-proxy.
Starting Anonymising Proxy Service: anon-proxy.
chris@chris-desktop:~$ 


---

### Post by chrisbish on 2007-06-23
Found it its called:

Network Proxy

i can't find any were to remove it.

---

### Post by bapoumba on 2007-06-23
Please run:
```
gnome-network-preferences
``` 
is it set to direct?

Look in synaptic (the menu relative to network or something close in Preferences), any proxy ?

Look at those files:
```
cat /etc/apt/apt.conf
cat /etc/environment
cat .bashrc 
```
Is there any reference to a proxy ?

---

### Post by chrisbish on 2007-06-23
the code you told me to run opend up the options of the network proxy

as i said in my last post

i need a way of uninstalling it some how.

---

### Post by chrisbish on 2007-06-23
ive found the program folder 
in etc

can i just delete it or will it screw something up?

---

### Post by bapoumba on 2007-06-23
> **chrisbish said:**
> the code you told me to run opend up the options of the network proxy

as i said in my last post

i need a way of uninstalling it some how.
and in **gnome-network-preferences** can you set it to direct?

What packages did you install?

---

### Post by chrisbish on 2007-06-23
i can set it to direct
the package was called network proxy i think.

---

### Post by chrisbish on 2007-06-23
its already on direct .

---

### Post by bapoumba on 2007-06-23
> **chrisbish said:**
> i can set it to direct
the package was called network proxy i think.
So set it to direct, and run:
```
sudo aptitude update
```
Do you get any error ? (paste the in here)

Please run
```
aptitude search proxy
```
and see which packages are installed (with an "i" at the beginning of the line). Paste the output if you're not sure.

---

### Post by chrisbish on 2007-06-23
first code:
> chris@chris-desktop:~$ sudo aptitude update
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
chris@chris-desktop:~$ 



second:
> chris@chris-desktop:~$ aptitude search proxy
i   anon-proxy                      - Proxy to surf the web anonymously         
p   apt-proxy                       - Debian archive proxy and partial mirror bu
p   connect-proxy                   - Establish TCP connection using SOCKS4/5 an
p   ctrlproxy                       - An IRC proxy with multiserver support     
p   dircproxy                       - IRC proxy for people who use IRC from diff
p   ffproxy                         - A light and customizable http(s) proxy ser
p   filterproxy                     - A filtering proxy, which can among other t
p   ftp-proxy                       - application level proxy for the FTP protoc
p   imapproxy                       - IMAP protocol proxy                       
p   libapache2-mod-proxy-html       - Apache2 filter module for HTML links rewri
p   libhttp-proxy-perl              - A pure Perl HTTP proxy                    
p   libroxen-telnetproxy            - Telnet proxy module for the Roxen Challeng
p   micro-proxy                     - really small HTTP/HTTPS proxy             
p   pcproxy                         - A masquerading proxy for flight simulation
p   proxychains                     - proxy chains - redirect connections throug
p   proxycheck                      - checks existence of open proxy            
p   proxytrack                      - Build HTTP Caches using archived websites 
p   python-egenix-mxproxy           - generic proxy wrapper type for Python     
v   python-egenix-mxproxy-dbg       -                                           
v   python2.4-egenix-mxproxy        -                                           
v   python2.5-egenix-mxproxy        -                                           
p   rtpproxy                        - Relay media streams (RTP/ VoIP) through an
p   simpleproxy                     - Simple TCP proxy                          
i   smproxy                         - X client - smproxy                        
p   spikeproxy                      - Web application security testing proxy    
p   tidy-proxy                      - A small http proxy which tidies html      
p   tinyproxy                       - A lightweight, non-caching, optionally ano
p   transproxy                      - Transparent Proxy Daemon for HTTP requests
p   ucspi-proxy                     - Connection proxy for UCSPI tools          
chris@chris-desktop:~$ 


---

### Post by bapoumba on 2007-06-23
OK, the package is anon-proxy.

How did you install it? aptitude, apt-get or synaptic?

---

### Post by chrisbish on 2007-06-23
synaptic package manger i used so it must be synaptic

---

### Post by bapoumba on 2007-06-23
So open synaptic and remove anon-proxy from there.
Edit: might want to purge it, in order to remove the conf files associated with it.

---

### Post by chrisbish on 2007-06-23
it worked

thankyou :)

---

