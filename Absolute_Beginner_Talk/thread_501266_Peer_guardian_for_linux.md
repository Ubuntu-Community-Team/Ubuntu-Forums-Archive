---
title: "Peer guardian for linux?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-07-15
Is there any program like Peer Gaurdian for linux.  I like to use these types of programs when downloading torrents.

Thx,

VC

---

### Post by kevinlyfellow on 2007-07-15
According to the PeerGuardian site, they recommend MoBlock.  [http://moblock.berlios.de/](http://moblock.berlios.de/)

---

### Post by videocheez on 2007-07-15
Thanks for the tip.  Duh, i should have looked their.  Anyways,  I followed the following:

```

deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main

Run these commands (on command line) to accept the new entries in sources.list. Adding the key to the apt keyring may be optional depending on your system's settings.

gpg --keyserver subkeys.pgp.net --recv DEDA0559 

gpg --export --armor DEDA0559 | sudo apt-key add -



sudo apt-get install moblock-nfq


```

It appeared to have installed properly but I can tell if its running or know how to run it.  If I open terminal and type moblock, I get the following:

don1@don1-ubuntu:~$ moblock

MoBlock 0.8 by Morpheus
Syntax: MoBlock -dnp <blocklist> [-b] [-q 0-65535] <logfile>

        -d      blocklist is an ipfilter.dat file
        -n      blocklist is a peerguardian 2.x file (.p2b)
        -p      blocklist is a peerguardian file (.p2p)
        -q      0-65535 NFQUEUE number (as specified in --queue-num with iptables)

Does anyone know what this means.

Thx in advance,

VC

---

### Post by kevinlyfellow on 2007-07-15
From what I gather, I think moblock is in started at bootup

see what the output of 
```
sudo /etc/init.d/moblock-nfq start
```

I think it is probably running.  Have you set anything up (like a blacklist file) or have you only installed it?

---

### Post by Malibu Illusion on 2007-07-15
```
ps aux | egrep moblock
```

It also runs a cronjob to update the filters daily located in /etc/cron.daily/

Take care.

---

### Post by videocheez on 2007-07-16
> **kevinlyfellow said:**
> From what I gather, I think moblock is in started at bootup

see what the output of 
```
sudo /etc/init.d/moblock-nfq start
```

I think it is probably running.  Have you set anything up (like a blacklist file) or have you only installed it?

I followed your suggestion and received the following:
don1@don1-ubuntu:~$ sudo /etc/init.d/moblock-nfq start
Password:
Sorry, try again.
Password:
 * Starting moblock moblock 

[QUOTE=Malibu Illusion] 
Code:

ps aux | egrep moblock

It also runs a cronjob to update the filters daily located in /etc/cron.daily/
[/QUOTE]

I entered your suggested code and received the following:

don1@don1-ubuntu:~$ ps aux | egrep moblock
root      4815  0.0  0.1   1716   444 ?        Ss   18:52   0:00 /bin/sh /etc/moblock/MoBlock-nfq.sh -p /etc/moblock/guarding.p2p -q 0 /var/log/moblock.log
root      4903  0.1  6.5  25612 16816 ?        S    18:52   0:17 /usr/bin/moblock -p /etc/moblock/guarding.p2p -q 0 /var/log/moblock.log

I assume that it is working but I'm not sure because I was able to go to intenet movie database website and I have no visual indicator like I did with Peer Guardian. I suppose I could live with no vidual indicator as long as I know that it's working and how to interpret the sources of the blocked IP's.  Is there no GUI?

Thx,

VC

---

### Post by kevinlyfellow on 2007-07-17
> **videocheez said:**
> I followed your suggestion and received the following:
don1@don1-ubuntu:~$ sudo /etc/init.d/moblock-nfq start
Password:
Sorry, try again.
Password:
 * Starting moblock moblock 



I entered your suggested code and received the following:

don1@don1-ubuntu:~$ ps aux | egrep moblock
root      4815  0.0  0.1   1716   444 ?        Ss   18:52   0:00 /bin/sh /etc/moblock/MoBlock-nfq.sh -p /etc/moblock/guarding.p2p -q 0 /var/log/moblock.log
root      4903  0.1  6.5  25612 16816 ?        S    18:52   0:17 /usr/bin/moblock -p /etc/moblock/guarding.p2p -q 0 /var/log/moblock.log

I assume that it is working but I'm not sure because I was able to go to intenet movie database website and I have no visual indicator like I did with Peer Guardian. I suppose I could live with no vidual indicator as long as I know that it's working and how to interpret the sources of the blocked IP's.  Is there no GUI?

Thx,

VC

Excellent!  We know it runs.  You can check logs, but I don't know if they will tell you what you need to know.  It is in /var/log/moblock.log  There was talk about making a gui.

[http://ubuntuforums.org/showthread.php?t=192559&page=9&highlight=moblock+gui](http://ubuntuforums.org/showthread.php?t=192559&page=9&highlight=moblock+gui)
and
[http://ubuntuforums.org/showthread.php?t=423626&highlight=moblock+gui](http://ubuntuforums.org/showthread.php?t=423626&highlight=moblock+gui)
and
here is an actual gui for download [http://ubuntuforums.org/showthread.php?t=461235](http://ubuntuforums.org/showthread.php?t=461235)

---

