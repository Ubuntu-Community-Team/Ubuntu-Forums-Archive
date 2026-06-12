---
title: "How do I go about checking if Moblock (PG) is on?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-08-02
I followed the instructions

> gpg --keyserver subkeys.pgp.net --recv DEDA0559 

gpg --export --armor DEDA0559 | sudo apt-key add -

sudo apt-get update


ajskhan@ubuntu:~$ gpg --keyserver subkeys.pgp.net --recv DEDA0559 
gpg: directory `/home/ajskhan/.gnupg' created
gpg: can't open `/gnupg/options.skel': No such file or directory
gpg: keyring `/home/ajskhan/.gnupg/secring.gpg' created
gpg: keyring `/home/ajskhan/.gnupg/pubring.gpg' created
gpg: requesting key DEDA0559 from hkp server subkeys.pgp.net
gpg: /home/ajskhan/.gnupg/trustdb.gpg: trustdb created
gpg: key DEDA0559: public key "clessing <clessing@users.sourceforge.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
ajskhan@ubuntu:~$ 
ajskhan@ubuntu:~$ gpg --export --armor DEDA0559 | sudo apt-key add -
Password:
OK
ajskhan@ubuntu:~$ gpg --keyserver subkeys.pgp.net --recv DEDA0559 
gpg: requesting key DEDA0559 from hkp server subkeys.pgp.net
gpg: key DEDA0559: "clessing <clessing@users.sourceforge.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
ajskhan@ubuntu:~$ 
ajskhan@ubuntu:~$ gpg --export --armor DEDA0559 | sudo apt-key add -
OK
ajskhan@ubuntu:~$ 
ajskhan@ubuntu:~$ sudo apt-get update
Get:1 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) unstable Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US  
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) unstable/main Translation-en_US       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) unstable Release              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) unstable/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) unstable/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 192B in 1s (155B/s)
Reading package lists... Done
ajskhan@ubuntu:~$ 
ajskhan@ubuntu:~$ sudo apt-get install moblock-nfq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libnetfilter-queue1 libnfnetlink1
The following NEW packages will be installed:
  libnetfilter-queue1 libnfnetlink1 moblock-nfq
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 45.2kB of archives.
After unpacking 217kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) unstable/main moblock-nfq 0.8-15 [30.9kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libnfnetlink1 0.0.16-1 [7582B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libnetfilter-queue1 0.0.12-1 [6716B]
Fetched 45.2kB in 0s (75.9kB/s)       
Selecting previously deselected package libnfnetlink1.
(Reading database ... 104883 files and directories currently installed.)
Unpacking libnfnetlink1 (from .../libnfnetlink1_0.0.16-1_i386.deb) ...
Selecting previously deselected package libnetfilter-queue1.
Unpacking libnetfilter-queue1 (from .../libnetfilter-queue1_0.0.12-1_i386.deb) ...
Selecting previously deselected package moblock-nfq.
Unpacking moblock-nfq (from .../moblock-nfq_0.8-15_i386.deb) ...
Setting up libnfnetlink1 (0.0.16-1) ...

Setting up libnetfilter-queue1 (0.0.12-1) ...

Setting up moblock-nfq (0.8-15) ...
moblock: checking for new block lists...
--15:43:12--  [http://www.bluetack.co.uk/](http://www.bluetack.co.uk/)
           => `-'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.bluetack.co.uk/forums/index.php](http://www.bluetack.co.uk/forums/index.php) [following]
--15:43:12--  [http://www.bluetack.co.uk/forums/index.php](http://www.bluetack.co.uk/forums/index.php)
           => `-'
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 112,975       --.--K/s             

15:43:13 (813.60 KB/s) - `-' saved [112975]

------------ 2007-08-02 03:43:13 PM EDT Begin PeerGuardian 
--15:43:13--  [http://www.bluetack.co.uk/config/ads-trackers-and-bad-pr0n.gz](http://www.bluetack.co.uk/config/ads-trackers-and-bad-pr0n.gz)
           => `ads-trackers-and-bad-pr0n.gz'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.bluetack.info/temp/ads-trackers-and-bad-pr0n.gz](http://www.bluetack.info/temp/ads-trackers-and-bad-pr0n.gz) [following]
--15:43:13--  [http://www.bluetack.info/temp/ads-trackers-and-bad-pr0n.gz](http://www.bluetack.info/temp/ads-trackers-and-bad-pr0n.gz)
           => `ads-trackers-and-bad-pr0n.gz'
Resolving [www.bluetack.info](www.bluetack.info)... 74.208.60.13
Connecting to www.bluetack.info|74.208.60.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31,499 (31K) [text/plain]

100%[====================================>] 31,499        --.--K/s             

15:43:13 (514.86 KB/s) - `ads-trackers-and-bad-pr0n.gz' saved [31499/31499]

--15:43:14--  [http://www.bluetack.co.uk/config/bogon.gz](http://www.bluetack.co.uk/config/bogon.gz)
           => `bogon.gz'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.bluetack.info/temp/bogon.gz](http://www.bluetack.info/temp/bogon.gz) [following]
--15:43:14--  [http://www.bluetack.info/temp/bogon.gz](http://www.bluetack.info/temp/bogon.gz)
           => `bogon.gz'
Resolving [www.bluetack.info](www.bluetack.info)... 74.208.60.13
Connecting to www.bluetack.info|74.208.60.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 32,934 (32K) [text/plain]

100%[====================================>] 32,934        --.--K/s             

15:43:14 (329.92 KB/s) - `bogon.gz' saved [32934/32934]

--15:43:14--  [http://www.bluetack.co.uk/config/dshield.gz](http://www.bluetack.co.uk/config/dshield.gz)
           => `dshield.gz'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.bluetack.nl/bluetack/dshield.gz](http://www.bluetack.nl/bluetack/dshield.gz) [following]
--15:43:14--  [http://www.bluetack.nl/bluetack/dshield.gz](http://www.bluetack.nl/bluetack/dshield.gz)
           => `dshield.gz'
Resolving [www.bluetack.nl](www.bluetack.nl)... 193.227.121.180
Connecting to www.bluetack.nl|193.227.121.180|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://bluetack4.snowmanuk.net/bluetack/dshield.gz](http://bluetack4.snowmanuk.net/bluetack/dshield.gz) [following]
--15:43:15--  [http://bluetack4.snowmanuk.net/bluetack/dshield.gz](http://bluetack4.snowmanuk.net/bluetack/dshield.gz)
           => `dshield.gz'
Resolving bluetack4.snowmanuk.net... 72.249.77.64
Connecting to bluetack4.snowmanuk.net|72.249.77.64|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,132 (2.1K) [text/plain]

100%[====================================>] 2,132         --.--K/s             

15:43:15 (33.56 MB/s) - `dshield.gz' saved [2132/2132]

--15:43:15--  [http://www.bluetack.co.uk/config/hijacked.gz](http://www.bluetack.co.uk/config/hijacked.gz)
           => `hijacked.gz'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.bluetack.nl/bluetack/hijacked.gz](http://www.bluetack.nl/bluetack/hijacked.gz) [following]
--15:43:15--  [http://www.bluetack.nl/bluetack/hijacked.gz](http://www.bluetack.nl/bluetack/hijacked.gz)
           => `hijacked.gz'
Resolving [www.bluetack.nl](www.bluetack.nl)... 193.227.121.180
Connecting to www.bluetack.nl|193.227.121.180|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://bluetack4.snowmanuk.net/bluetack/hijacked.gz](http://bluetack4.snowmanuk.net/bluetack/hijacked.gz) [following]
--15:43:15--  [http://bluetack4.snowmanuk.net/bluetack/hijacked.gz](http://bluetack4.snowmanuk.net/bluetack/hijacked.gz)
           => `hijacked.gz'
Resolving bluetack4.snowmanuk.net... 72.249.77.64
Connecting to bluetack4.snowmanuk.net|72.249.77.64|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 712 [text/plain]

100%[====================================>] 712           --.--K/s             

15:43:15 (13.67 MB/s) - `hijacked.gz' saved [712/712]

--15:43:15--  [http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz)
           => `level1.gz'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.btack.info/level1.gz](http://www.btack.info/level1.gz) [following]
--15:43:15--  [http://www.btack.info/level1.gz](http://www.btack.info/level1.gz)
           => `level1.gz'
Resolving [www.btack.info](www.btack.info)... 74.208.57.249
Connecting to www.btack.info|74.208.57.249|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://bluetack2.snowmanuk.net.nyud.net:8080/bluetack/level1.gz](http://bluetack2.snowmanuk.net.nyud.net:8080/bluetack/level1.gz) [following]
--15:43:15--  [http://bluetack2.snowmanuk.net.nyud.net:8080/bluetack/level1.gz](http://bluetack2.snowmanuk.net.nyud.net:8080/bluetack/level1.gz)
           => `level1.gz'
Resolving bluetack2.snowmanuk.net.nyud.net... 169.229.50.15, 169.229.50.11, 169.229.50.14
Connecting to bluetack2.snowmanuk.net.nyud.net|169.229.50.15|:8080... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,925,867 (2.8M) [text/plain]

100%[====================================>] 2,925,867    144.71K/s    ETA 00:00

15:43:30 (204.58 KB/s) - `level1.gz' saved [2925867/2925867]

--15:43:30--  [http://www.bluetack.co.uk/config/level2.gz](http://www.bluetack.co.uk/config/level2.gz)
           => `level2.gz'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://bluetack.info/level2.gz](http://bluetack.info/level2.gz) [following]
--15:43:30--  [http://bluetack.info/level2.gz](http://bluetack.info/level2.gz)
           => `level2.gz'
Resolving bluetack.info... 74.208.60.13
Connecting to bluetack.info|74.208.60.13|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://bluetack3.snowmanuk.net/bluetack/level2.gz](http://bluetack3.snowmanuk.net/bluetack/level2.gz) [following]
--15:43:30--  [http://bluetack3.snowmanuk.net/bluetack/level2.gz](http://bluetack3.snowmanuk.net/bluetack/level2.gz)
           => `level2.gz'
Resolving bluetack3.snowmanuk.net... 72.249.77.64
Connecting to bluetack3.snowmanuk.net|72.249.77.64|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 735,574 (718K) [text/plain]

100%[====================================>] 735,574      572.23K/s             

15:43:32 (570.29 KB/s) - `level2.gz' saved [735574/735574]

--15:43:32--  [http://www.bluetack.co.uk/config/Microsoft.gz](http://www.bluetack.co.uk/config/Microsoft.gz)
           => `Microsoft.gz'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.bluetack.nl/bluetack/Microsoft.gz](http://www.bluetack.nl/bluetack/Microsoft.gz) [following]
--15:43:32--  [http://www.bluetack.nl/bluetack/Microsoft.gz](http://www.bluetack.nl/bluetack/Microsoft.gz)
           => `Microsoft.gz'
Resolving [www.bluetack.nl](www.bluetack.nl)... 193.227.121.180
Connecting to www.bluetack.nl|193.227.121.180|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://bluetack4.snowmanuk.net/bluetack/Microsoft.gz](http://bluetack4.snowmanuk.net/bluetack/Microsoft.gz) [following]
--15:43:32--  [http://bluetack4.snowmanuk.net/bluetack/Microsoft.gz](http://bluetack4.snowmanuk.net/bluetack/Microsoft.gz)
           => `Microsoft.gz'
Resolving bluetack4.snowmanuk.net... 72.249.77.64
Connecting to bluetack4.snowmanuk.net|72.249.77.64|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12,427 (12K) [text/plain]

100%[====================================>] 12,427        --.--K/s             

15:43:32 (88.96 MB/s) - `Microsoft.gz' saved [12427/12427]

--15:43:32--  [http://www.bluetack.co.uk/config/spider.gz](http://www.bluetack.co.uk/config/spider.gz)
           => `spider.gz'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.bluetack.nl/bluetack/spider.gz](http://www.bluetack.nl/bluetack/spider.gz) [following]
--15:43:32--  [http://www.bluetack.nl/bluetack/spider.gz](http://www.bluetack.nl/bluetack/spider.gz)
           => `spider.gz'
Resolving [www.bluetack.nl](www.bluetack.nl)... 193.227.121.180
Connecting to www.bluetack.nl|193.227.121.180|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://bluetack4.snowmanuk.net/bluetack/spider.gz](http://bluetack4.snowmanuk.net/bluetack/spider.gz) [following]
--15:43:33--  [http://bluetack4.snowmanuk.net/bluetack/spider.gz](http://bluetack4.snowmanuk.net/bluetack/spider.gz)
           => `spider.gz'
Resolving bluetack4.snowmanuk.net... 72.249.77.64
Connecting to bluetack4.snowmanuk.net|72.249.77.64|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,852 (3.8K) [text/plain]

100%[====================================>] 3,852         --.--K/s             

15:43:33 (54.79 MB/s) - `spider.gz' saved [3852/3852]

--15:43:33--  [http://www.bluetack.co.uk/config/spyware.gz](http://www.bluetack.co.uk/config/spyware.gz)
           => `spyware.gz'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.bluetack.info/temp/spyware.gz](http://www.bluetack.info/temp/spyware.gz) [following]
--15:43:33--  [http://www.bluetack.info/temp/spyware.gz](http://www.bluetack.info/temp/spyware.gz)
           => `spyware.gz'
Resolving [www.bluetack.info](www.bluetack.info)... 74.208.60.13
Connecting to www.bluetack.info|74.208.60.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 28,917 (28K) [text/plain]

100%[====================================>] 28,917        --.--K/s             

15:43:33 (874.87 KB/s) - `spyware.gz' saved [28917/28917]

--15:43:33--  [http://www.bluetack.co.uk/config/templist.gz](http://www.bluetack.co.uk/config/templist.gz)
           => `templist.gz'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.bluetack.info/temp/templist.gz](http://www.bluetack.info/temp/templist.gz) [following]
--15:43:34--  [http://www.bluetack.info/temp/templist.gz](http://www.bluetack.info/temp/templist.gz)
           => `templist.gz'
Resolving [www.bluetack.info](www.bluetack.info)... 74.208.60.13
Connecting to www.bluetack.info|74.208.60.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,209 (8.0K) [text/plain]

100%[====================================>] 8,209         --.--K/s             

15:43:34 (56.69 MB/s) - `templist.gz' saved [8209/8209]

 * Reloading moblock moblock                                             [ OK ] 
 * Starting moblock moblock                                              [ OK ] 


Followed this: [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)
The grab it section.

It all went fine, few errors in the middle (that is why I am afraid...)

I just want to test if it is on and if it is blocking

So:
1. How do I test if it is on and blocking?
2. Does it auto update?

Thanks

(and yes I know the easiest way is to probably go download an ISO of vista or something, but whats the need with Ubuntu?)

---

### Post by milosz.galazka on 2007-08-02
Hello,

You can check if process is running by executing commands (for example I am checking if firefox is running)

```
ps ax | grep firefox | grep -v grep
```

I can write (checking) script for you at Saturday as I suppose I will spend that day at home...

---

### Post by chinaski on 2007-08-03
[http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock](http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock)

---

### Post by zanglang on 2007-08-03
1. Answered by milosz. You should see something like:
>  4800 ?        S      0:00 /bin/sh /etc/moblock/MoBlock-nfq.sh -p /etc/moblock/guarding.p2p -q 0 /var/log/moblock.log
 4871 ?        S      0:32 /usr/bin/moblock -p /etc/moblock/guarding.p2p -q 0 /var/log/moblock.log

2. Moblock installs with a daily cronjob that downloads the blocklists daily, so yep.

To test if it's actually working, randomly pick an IP from Moblock's blocklist and ping it for a few seconds. Moblock's log file should show it blocking the outgoing packets.
> zanglang@aesir:~$ tail -n 1 /etc/moblock/guarding.p2p
p2p Corrupt Data Senders:84.124.139.133-84.124.139.133
zanglang@aesir:~$ ping 84.124.139.133
PING 84.124.139.133 (84.124.139.133) 56(84) bytes of data.

--- 84.124.139.133 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

zanglang@aesir:~$ tail -n 3 /var/log/moblock.log
Blocked OUT: p2p Corrupt Data Senders,hits: 1,DST: 84.124.139.133
Blocked OUT: p2p Corrupt Data Senders,hits: 2,DST: 84.124.139.133
Blocked OUT: p2p Corrupt Data Senders,hits: 3,DST: 84.124.139.133

---

### Post by chinaski on 2007-08-03
```
~$ tail -f /var/log/moblock.log
```you'll see the real-time output in terminal window

[[IMG]http://img398.imageshack.us/img398/8162/screenshotzastation1pi3.png[/IMG]]("http://imageshack.us")

---

### Post by ajskhan on 2007-08-07
awesome guys
it works!

---

