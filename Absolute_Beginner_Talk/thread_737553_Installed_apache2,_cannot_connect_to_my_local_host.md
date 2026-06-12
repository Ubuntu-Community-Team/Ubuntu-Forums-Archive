---
title: "Installed apache2, cannot connect to my local host"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by ouselesso on 2008-03-27
Hello all, I just installed apache2 on my gusty box and when I try to connect to localhost in a web browser it doesn't load just times out. Any ideas as to why i cannot connect locally? i 

installed from terminal
 ```
jgallios@JGallios-Ubuntu:~$ sudo apt-get install apache2
[sudo] password for jgallios:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libarts1c2a kdelibs4c2a libartsc0 fftw3 kdelibs-data liblualib50 ruby1.8 kdebase-kio-plugins
  python-qt3 ruby libkonq4 libavahi-qt3-1 python-sip4 kdebase-bin libtunepimp5 libifp4 libdbus-qt-1-1c2 kdesktop
  libqt3-mt liblua50 libruby1.8 libnjb5 libofa0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-worker apache2-utils apache2.2-common libapr1 libaprutil1 libpq5
Suggested packages:
  apache2-doc
The following NEW packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-common libapr1 libaprutil1 libpq5
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2190kB of archives.
After unpacking 6218kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libapr1.
(Reading database ... 112861 files and directories currently installed.)
Unpacking libapr1 (from .../libapr1_1.2.7-8.2ubuntu1_i386.deb) ...
Selecting previously deselected package libpq5.
Unpacking libpq5 (from .../libpq5_8.2.6-0ubuntu0.7.10.1_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.7+dfsg-2build1_i386.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.2.4-3ubuntu0.1_i386.deb) ...
Selecting previously deselected package apache2.2-common.
Unpacking apache2.2-common (from .../apache2.2-common_2.2.4-3ubuntu0.1_i386.deb) ...
Selecting previously deselected package apache2-mpm-worker.
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.2.4-3ubuntu0.1_i386.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.2.4-3ubuntu0.1_all.deb) ...
Setting up libapr1 (1.2.7-8.2ubuntu1) ...

Setting up libpq5 (8.2.6-0ubuntu0.7.10.1) ...

Setting up libaprutil1 (1.2.7+dfsg-2build1) ...

Setting up apache2-utils (2.2.4-3ubuntu0.1) ...
Setting up apache2.2-common (2.2.4-3ubuntu0.1) ...

Setting up apache2-mpm-worker (2.2.4-3ubuntu0.1) ...
 * Starting web server apache2                                                                              [ OK ] 

Setting up apache2 (2.2.4-3ubuntu0.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

---

### Post by sillyxone on 2008-03-27
run this and post output:

```
sudo /etc/init.d/apache2 restart
```

also, look into /var/log/apache2/error.log for clues

---

### Post by ouselesso on 2008-03-27
restarted apache yielded these results
```
jgallios@JGallios-Ubuntu:~$ sudo /etc/init.d/apache2 restart
[sudo] password for jgallios:
 * Restarting web server apache2                                                                            [ OK ] 
jgallios@JGallios-Ubuntu:~$ 

```

Looked at the log, nothing that would catch my attention no error messages
```
[Thu Mar 27 15:44:11 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Mar 27 15:44:21 2008] [notice] Apache/2.2.4 (Ubuntu) configured -- resuming normal operations
```

---

### Post by sillyxone on 2008-03-27
how about try 127.0.0.1 in your browser?

also, try "netstat -a | grep http", see if you get anything

oh, did you mention it timed out? or the browser just says "Unable to connect"? If I turn off Apache, Firefox just say "Unable to connect" when I type in localhost.

---

### Post by ouselesso on 2008-03-27
When i run netstat -a | grep http I get no results. If I try to load from my IP on another computer the browser pulls it up just fine, but on gutsy box i cant connect locally
[indent]The connection has timed out
The server at 127.0.0.1 is taking too long to respond.[/indent]

---

### Post by sillyxone on 2008-03-28
not sure what might be wrong, but seems to be the client on the same machine. Try a different browser, or clear the cache. Also check to see if firewall or proxy is running that is blocking/rerouting local requests.

try to ping 127.0.0.1 or ping localhost and see if you can reach yourself. Also, you can use ifconfig to make sure that "local loopback" device is there, if not, try to bring it up "sudo ifconfig lo up"

---

