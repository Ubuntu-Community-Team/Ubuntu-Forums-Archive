---
title: "flash wont install, now synaptic broke &amp; cant use dpkg configure"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-02-24
i tried to get flash working earlier using that psychocats page but method1 dont work so tried method2, got stuck partway thru cuz kept timing out. tried synaptic & the add/remove it timed out, and i get errors trying to use any of em now. here's my latest try @method2

```

gail@gail-oldpos:~$ sudo apt-get remove flashplugin-nonfree
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
gail@gail-oldpos:~$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (9.0.31.0.1ubuntu1~edgy1) ...
Downloading...
--20:59:29--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 1.0.0.0
Connecting to fpdownload.macromedia.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--21:02:39--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
  (try: 2) => `./install_flash_player_9_linux.tar.gz'
Connecting to fpdownload.macromedia.com|1.0.0.0|:80... 

```

---

### Post by taurus on 2007-02-24
Maybe the site is down!  However, this is a little trouble here, fpdownload.macromedia.com|1.0.0.0|:80.

See if your network connection is still good.

```
ping -c 3 www.google.com
```

---

### Post by lunaz on 2007-02-24
gail@gail-oldpos:~$ ping -c 3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.102.7.147) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (66.102.7.147): icmp_seq=1 ttl=243 time=60.5 ms
64 bytes from [www.google.com](www.google.com) (66.102.7.147): icmp_seq=2 ttl=243 time=60.5 ms
64 bytes from [www.google.com](www.google.com) (66.102.7.147): icmp_seq=3 ttl=243 time=58.3 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 58.369/59.833/60.571/1.054 ms
gail@gail-oldpos:~$

---

### Post by taurus on 2007-02-24
What happens when you run this?

```
sudo aptitude update
```

---

### Post by lunaz on 2007-02-24
so far it just keeps timing out :(

```

gail@gail-oldpos:~$ ping -c 3 www.google.com
PING www.l.google.com (66.102.7.147) 56(84) bytes of data.
64 bytes from www.google.com (66.102.7.147): icmp_seq=1 ttl=243 time=60.5 ms
64 bytes from www.google.com (66.102.7.147): icmp_seq=2 ttl=243 time=60.5 ms
64 bytes from www.google.com (66.102.7.147): icmp_seq=3 ttl=243 time=58.3 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 58.369/59.833/60.571/1.054 ms
gail@gail-oldpos:~$ sudo aptitude update
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Err http://archive.ubuntu.com edgy Release.gpg                                               
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com edgy-security Release.gpg                                     
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com edgy/universe Translation-en_CA                                
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com edgy-security/main Translation-en_CA                          
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

```

---

### Post by taurus on 2007-02-24
Any change you have a proxy on your machine?

This command runs fine on my machine.
```
ping -c 3 security.ubuntu.com
```

```

PING security.ubuntu.com (82.211.81.138) 56(84) bytes of data.
64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=0 ttl=44 time=115 ms
64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=1 ttl=44 time=115 ms
64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=2 ttl=44 time=116 ms

--- security.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 115.560/115.784/116.001/0.432 ms, pipe 2

```

---

### Post by lunaz on 2007-02-24
```

gail@gail-oldpos:~$ ping -c 3 security.ubuntu.com
PING security.ubuntu.com (82.211.81.138) 56(84) bytes of data.
64 bytes from security.ubuntu.com (82.211.81.138): icmp_seq=1 ttl=50 time=208 ms
64 bytes from security.ubuntu.com (82.211.81.138): icmp_seq=2 ttl=50 time=208 ms
64 bytes from security.ubuntu.com (82.211.81.138): icmp_seq=3 ttl=50 time=208 ms

--- security.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 208.217/208.381/208.544/0.395 ms
gail@gail-oldpos:~$ 

```

i dunno how to check for proxy.

---

### Post by lunaz on 2007-02-25
i went to system>networking>dns & removed the 192.168.0.1 from services. i always have to do that to get gaim working lol... so i did that, got on gaim, now tried sudo aptitude update and ...

```

gail@gail-oldpos:~$ sudo aptitude update
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_CA
Ign http://security.ubuntu.com edgy-security/universe Translation-en_CA
Hit http://security.ubuntu.com edgy-security Release        
Hit http://security.ubuntu.com edgy-security/main Packages  
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://security.ubuntu.com edgy-security/universe Sources
Get:2 http://archive.ubuntu.com edgy Release.gpg [191B]     
Ign http://archive.ubuntu.com edgy/universe Translation-en_CA
Ign http://archive.ubuntu.com edgy/main Translation-en_CA
Ign http://archive.ubuntu.com edgy/restricted Translation-en_CA
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_CA
Get:3 http://archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_CA
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_CA
Get:4 http://archive.ubuntu.com edgy-backports Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_CA
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_CA
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_CA
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_CA
Hit http://archive.ubuntu.com edgy Release
Hit http://archive.ubuntu.com edgy-updates Release
Hit http://archive.ubuntu.com edgy-backports Release
Hit http://archive.ubuntu.com edgy/main Sources
Hit http://archive.ubuntu.com edgy/restricted Sources
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy/main Packages
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages
Hit http://archive.ubuntu.com edgy/universe Sources
Hit http://archive.ubuntu.com edgy-updates/main Packages
Hit http://archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-updates/main Sources
Hit http://archive.ubuntu.com edgy-updates/restricted Sources
Hit http://archive.ubuntu.com edgy-backports/main Packages
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://archive.ubuntu.com edgy-backports/main Sources
Hit http://archive.ubuntu.com edgy-backports/restricted Sources
Hit http://archive.ubuntu.com edgy-backports/universe Sources
Hit http://archive.ubuntu.com edgy-backports/multiverse Sources
Fetched 194B in 5s (37B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache
gail@gail-oldpos:~$ 

```

omg what did i break? lol oO

edit: woah i think it worked.

```

gail@gail-oldpos:~$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (9.0.31.0.1ubuntu1~edgy1) ...
Downloading...
--22:04:07--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.106.70
Connecting to fpdownload.macromedia.com|72.246.106.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,609,703 (2.5M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   26.88 KB/s
   50K .......... .......... .......... .......... ..........  3%   26.94 KB/s
  100K .......... .......... .......... .......... ..........  5%   25.94 KB/s
AND A BUNCH MORE OF THESE ...
 2500K .......... .......... .......... .......... ........  100%   26.95 KB/s

22:05:44 (26.42 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [2609703/2609703]

Download done.
Flash Plugin installed.

```

---

### Post by taurus on 2007-02-25
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

