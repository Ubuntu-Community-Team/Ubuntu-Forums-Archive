---
title: "machine only visible locally..."
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by 13ojo on 2007-03-31
hi,

title pretty much describes it.
i have a server setup, and i can SSH and view the apache2 stuff locally easily.

however, if i put in the ip address of my interent (like my id address when i get it from a webpage). it just times out. i have redirects from the router to the machine, on ports 22, 80, and 8080. now im geussing the machine must have some kind of firewall?.

it needs to allow me to SSH and use the web to it. cause im thinking about using no-ip's services to set ip up so i can monitor my server and what it's doing from uni :D.

---

### Post by Jussi Kukkonen on 2007-03-31
Ubuntu does not have a firewall by default. I've setup the exact system you describe without problems.

There are 3 levels of testing you can do here:
 * ping/ssh localhost
 * ping/ssh local ip (192.168.x.x usually)
 * ping/ssh external ip
If the first two work, the problem is in your router (or ISP blocking the port).

I suggest you set up key-based ssh logins by the way: password knocking is rampant nowadays.

---

### Post by 13ojo on 2007-03-31
23 enabled TCP 6881 6999 192.168.0.200 
24 enabled TCP 80 80 192.168.0.200 
25 enabled TCP 22 22 192.168.0.200 
26 enabled TCP 8080 8080 192.168.0.200 


those are the entries in my router for forwarding the ports.

step one and two work fine from any machine, step 3 i can ping from any machine, but cant ssh in?.

my isp is iinet (western australia) and they have port blocking options which are disabled.

bojo@server:~$ ssh [interenet ip]
ssh: connect to host [internet ip] port 22: Connection refused

ps. if you can help me access it from anywhere, i would like to have the key based logins to. but currently no one outside of 192.168.x.x can access the machine anyway.

is what happens when i try to ssh into the machine..... port forwarding is working for the bittorrent ports.

---

### Post by 13ojo on 2007-04-01
> [Sun Apr 01 06:25:34 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
Traceback (most recent call last):
  File "/usr/bin/tfQManager.torrentflux", line 428, in ?
    run(argv[1],argv[2],argv[3],argv[4],argv[5])
  File "/usr/bin/tfQManager.torrentflux", line 38, in run
    f=open(qDirectory+"tfQManager.pid",'w')
IOError: [Errno 13] Permission denied: '/home/bojo/BitTorrenttfQManager.pid'
grep: Downloads/.torrents/: No such file or directory
grep: write error: Broken pipe
Traceback (most recent call last):
  File "/usr/bin/tfQManager.torrentflux", line 428, in ?
    run(argv[1],argv[2],argv[3],argv[4],argv[5])
  File "/usr/bin/tfQManager.torrentflux", line 38, in run
    f=open(qDirectory+"tfQManager.pid",'w')
IOError: [Errno 13] Permission denied: '/home/bojo/BitTorrenttfQManager.pid'
grep: Downloads/.torrents/: No such file or directory
Traceback (most recent call last):
  File "/usr/bin/tfQManager.torrentflux", line 428, in ?
    run(argv[1],argv[2],argv[3],argv[4],argv[5])
  File "/usr/bin/tfQManager.torrentflux", line 38, in run
    f=open(qDirectory+"tfQManager.pid",'w')
IOError: [Errno 13] Permission denied: '/home/bojo/BitTorrenttfQManager.pid'
Traceback (most recent call last):
  File "/usr/bin/tfQManager.torrentflux", line 428, in ?
    run(argv[1],argv[2],argv[3],argv[4],argv[5])
  File "/usr/bin/tfQManager.torrentflux", line 38, in run
    f=open(qDirectory+"tfQManager.pid",'w')
IOError: [Errno 13] Permission denied: '/home/bojo/BitTorrenttfQManager.pid'
grep: Downloads/.torrents/: No such file or directory
grep: write error: Broken pipe
Traceback (most recent call last):
  File "/usr/bin/tfQManager.torrentflux", line 428, in ?
    run(argv[1],argv[2],argv[3],argv[4],argv[5])
  File "/usr/bin/tfQManager.torrentflux", line 38, in run
    f=open(qDirectory+"tfQManager.pid",'w')
IOError: [Errno 13] Permission denied: '/home/bojo/BitTorrenttfQManager.pid'
grep: Downloads/.torrents/: No such file or directory
Traceback (most recent call last):
  File "/usr/bin/tfQManager.torrentflux", line 428, in ?
    run(argv[1],argv[2],argv[3],argv[4],argv[5])
  File "/usr/bin/tfQManager.torrentflux", line 38, in run
    f=open(qDirectory+"tfQManager.pid",'w')
IOError: [Errno 13] Permission denied: '/home/bojo/BitTorrenttfQManager.pid'
grep: Downloads/.torrents/: No such file or directory
grep: write error: Broken pipe
Traceback (most recent call last):
  File "/usr/bin/tfQManager.torrentflux", line 428, in ?
    run(argv[1],argv[2],argv[3],argv[4],argv[5])
  File "/usr/bin/tfQManager.torrentflux", line 38, in run
    f=open(qDirectory+"tfQManager.pid",'w')
IOError: [Errno 13] Permission denied: '/home/bojo/BitTorrenttfQManager.pid'
grep: Downloads/.torrents/: No such file or directory
Traceback (most recent call last):
  File "/usr/bin/tfQManager.torrentflux", line 428, in ?
    run(argv[1],argv[2],argv[3],argv[4],argv[5])
  File "/usr/bin/tfQManager.torrentflux", line 38, in run
    f=open(qDirectory+"tfQManager.pid",'w')
IOError: [Errno 13] Permission denied: '/home/bojo/BitTorrenttfQManager.pid'
grep: Downloads/.torrents/: No such file or directory
grep: write error: Broken pipe
Traceback (most recent call last):
  File "/usr/bin/tfQManager.torrentflux", line 428, in ?
    run(argv[1],argv[2],argv[3],argv[4],argv[5])
  File "/usr/bin/tfQManager.torrentflux", line 38, in run
    f=open(qDirectory+"tfQManager.pid",'w')
IOError: [Errno 13] Permission denied: '/home/bojo/BitTorrenttfQManager.pid'
grep: Downloads/.torrents/: No such file or directory
Traceback (most recent call last):
  File "/usr/bin/tfQManager.torrentflux", line 428, in ?
    run(argv[1],argv[2],argv[3],argv[4],argv[5])
  File "/usr/bin/tfQManager.torrentflux", line 38, in run
    f=open(qDirectory+"tfQManager.pid",'w')
IOError: [Errno 13] Permission denied: '/home/bojo/BitTorrenttfQManager.pid'
grep: Downloads/.torrents/: No such file or directory
grep: write error: Broken pipe
ls: /var/www/TF_BitTornado/btphptornado.py: No such file or directory
ls: /var/www/TF_BitTornado/btshowmetainfo.py: No such file or directory
ls: /var/www/TF_BitTornado/btmakemetafile.py: No such file or directory
ls: /var/www/torrentflux/btphptornado.py: No such file or directory
ls: /var/www/torrentflux/btshowmetainfo.py: No such file or directory
ls: /var/www/torrentflux/btmakemetafile.py: No such file or directory
[Sun Apr 01 11:53:55 2007] [error] [client 192.168.0.4] File does not exist: /usr/share/torrentflux, referer: [http://192.168.0.200/](http://192.168.0.200/)
[Sun Apr 01 11:53:55 2007] [error] [client 192.168.0.4] File does not exist: /var/www/phpmyadmin/favicon.ico
[Sun Apr 01 11:53:55 2007] [error] [client 192.168.0.4] File does not exist: /var/www/favicon.ico
[Sun Apr 01 11:59:38 2007] [error] [client 192.168.0.4] File does not exist: /var/www/themes, referer: [http://192.168.0.200/phpmyadmin/db_create.php](http://192.168.0.200/phpmyadmin/db_create.php)
[Sun Apr 01 12:00:25 2007] [error] [client 192.168.0.4] File does not exist: /var/www/themes, referer: [http://192.168.0.200/phpmyadmin/db_import.php?db=torrentflux&token=cbd193fed221d0ca144e1282f98c28be&goto=db_details_structure.php](http://192.168.0.200/phpmyadmin/db_import.php?db=torrentflux&token=cbd193fed221d0ca144e1282f98c28be&goto=db_details_structure.php)
[Sun Apr 01 12:01:38 2007] [error] [client 192.168.0.4] File does not exist: /var/www/themes, referer: [http://192.168.0.200/phpmyadmin/db_details_structure.php?db=torrentflux&token=cbd193fed221d0ca144e1282f98c28be](http://192.168.0.200/phpmyadmin/db_details_structure.php?db=torrentflux&token=cbd193fed221d0ca144e1282f98c28be)
[Sun Apr 01 12:01:45 2007] [error] [client 192.168.0.4] File does not exist: /var/www/themes, referer: [http://192.168.0.200/phpmyadmin/db_operations.php?db=torrentflux&token=cbd193fed221d0ca144e1282f98c28be&goto=db_details_structure.php](http://192.168.0.200/phpmyadmin/db_operations.php?db=torrentflux&token=cbd193fed221d0ca144e1282f98c28be&goto=db_details_structure.php)
[Sun Apr 01 12:01:57 2007] [error] [client 192.168.0.4] File does not exist: /var/www/themes, referer: [http://192.168.0.200/phpmyadmin/db_details.php?db=torrentflux&token=cbd193fed221d0ca144e1282f98c28be&goto=db_operations.php&db_query_force=1](http://192.168.0.200/phpmyadmin/db_details.php?db=torrentflux&token=cbd193fed221d0ca144e1282f98c28be&goto=db_operations.php&db_query_force=1)
[Sun Apr 01 12:02:00 2007] [error] [client 192.168.0.4] File does not exist: /var/www/themes, referer: [http://192.168.0.200/phpmyadmin/db_import.php?db=torrentflux&token=cbd193fed221d0ca144e1282f98c28be](http://192.168.0.200/phpmyadmin/db_import.php?db=torrentflux&token=cbd193fed221d0ca144e1282f98c28be)
grep: Downloads/.torrents/: No such file or directory
grep: Downloads/.torrents/: No such file or directory
grep: write error: Broken pipe
grep: Downloads/.torrents/: No such file or directory
cd: 1: can't cd to /home/bojo/BitTorrent
sh: Downloads/: not found
grep: Downloads/.torrents/: No such file or directory
Traceback (most recent call last):
  File "/var/www/html/TF_BitTornado/btphptornado.py", line 451, in ?
    run(argv[1],argv[2],argv[3],argv[4],argv[5:])
  File "/var/www/html/TF_BitTornado/btphptornado.py", line 397, in run
    config, response, infohash, myid, rawserver, listen_port)
  File "/var/www/html/TF_BitTornado/BitTornado/download_bt1.py", line 351, in __init__
    self.appdataobj = ConfigDir()
  File "/var/www/html/TF_BitTornado/BitTornado/ConfigDir.py", line 99, in __init__
    os.mkdir(self.dir_root,0700)    # exception if failed
OSError: [Errno 13] Permission denied: '/var/www/.BitTornado'
grep: Downloads/.torrents/: No such file or directory
grep: write error: Broken pipe
grep: Downloads/.torrents/: No such file or directory
grep: write error: Broken pipe
cd: 1: can't cd to /home/bojo/BitTorrent
sh: Downloads/: not found
grep: Downloads/.torrents/: No such file or directory
Traceback (most recent call last):
  File "/var/www/html/TF_BitTornado/btphptornado.py", line 451, in ?
    run(argv[1],argv[2],argv[3],argv[4],argv[5:])
  File "/var/www/html/TF_BitTornado/btphptornado.py", line 397, in run
    config, response, infohash, myid, rawserver, listen_port)
  File "/var/www/html/TF_BitTornado/BitTornado/download_bt1.py", line 351, in __init__
    self.appdataobj = ConfigDir()
  File "/var/www/html/TF_BitTornado/BitTornado/ConfigDir.py", line 99, in __init__
    os.mkdir(self.dir_root,0700)    # exception if failed
OSError: [Errno 13] Permission denied: '/var/www/.BitTornado'
grep: Downloads/.torrents/: No such file or directory


apache logs...

---

### Post by Jussi Kukkonen on 2007-04-01
> **13ojo said:**
> 
step one and two work fine from any machine, step 3 i can ping from any machine, but cant ssh in?.

Ok. Your router probably answers the pings from internet side. I guess you could try removing the router from the loop for debug purposes, and connect your machine straight to the internet (just to check if the ISP port blocking really is turned off). Otherwise I can't think of anything else.

---

### Post by 13ojo on 2007-04-01
okay, the router is the actually internet connection.. so that's a no go.

it does seem to work however, i gave a friend my ip over a instant messenger client, and he was able to view my web-pages!.

i just cant view them here via entering my ip?, any idea.

---

### Post by 13ojo on 2007-07-07
any tech heads know the answer to this?.

It's not actually a problem, aside from fears that the web page won't be visible when i leave my house and i can't check it haha :(.

Just seems to be local ips=fine. External people using my IP/redirect = fine. But using the external IP on the local network =  timeout.

---

### Post by kosmic on 2007-07-07
Ok just let check if its your Internet provider that is blocking acess to your machine.

Go to :

[http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2)


and choose "All Service Ports"

After the program run see if it says that you port 22 is open, if it says that is closed and you are sure that you opened port 22 in you router, then is Your Internet Provider that is blocking acess to your computer.


EDIT :

Forget what i've said...

You said :

But using the external IP on the local network =  timeout.

You can't use your external IP on you inside network, The reason is that there is no gateway configured, so the computer in you local network don't know where to go, to get your IP...

In this case you only have 1 solution, change Internet Provider ou send them a letter asking to open ports...but i doub they will do it...

In Portugal we have one ISP that does that SAPO and Telepac :(

---

