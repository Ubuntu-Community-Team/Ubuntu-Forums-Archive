---
title: "Bind under ubuntu"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by extase on 2005-12-29
hi. 

I am actually trying to configure a bind9 server under ubuntu 5.10. 

When i restart the server the output is the following: 
```

/etc/init.d/bind9 restart
 * Stopping domain name service...                                              rndc: connect failed: connection refused
                                                                         [ ok ]
 * Starting domain name service...                                       [ ok ]


```

So i presumed the server was working 100% ....

But, no... Any client got any kind of hosts informations from server. I checked out with a sniffer, and the server does not responds to the dns requests. 

So i nmaped the server host. The output is the following:

```

nmap 127.0.0.1

Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-12-29 04:54 WET
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1659 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
22/tcp   open  ssh
631/tcp  open  ipp
1025/tcp open  NFS-or-IIS
1026/tcp open  LSA-or-nterm


```

Anyone has some tip? 

:confused: :confused: :confused: :confused:

---

### Post by Koybe on 2005-12-29
As you can see you add a problem with rndc. Propably a little misconfiguration in your config files. Cane you put the output of :

```
named-checkconf
named-checkzone yourdomain.org /path/to/your/zone.file
```

---

### Post by extase on 2005-12-29
Hi. 

For "named-checkconf" i got the following output: 

```
 
root@matrix:/etc# named-checkconf
root@matrix:/etc#

```

(its ok) 

For named-checkzone i had some errors: 

```


root@matrix:/etc# named-checkzone casaçlan  /etc/bind/db.casa.lan
/etc/bind/db.casa.lan:10: casa\231lan: bad owner name (check-names)
/etc/bind/db.casa.lan:12: ns.casa\231lan: bad owner name (check-names)
/etc/bind/db.casa.lan:13: matrix.casa\231lan: bad owner name (check-names)
/etc/bind/db.casa.lan:14: mail.casa\231lan: bad owner name (check-names)
/etc/bind/db.casa.lan:15: neo.casa\231lan: bad owner name (check-names)
/etc/bind/db.casa.lan:16: apoc.casa\231lan: bad owner name (check-names)
/etc/bind/db.casa.lan:17: trinity.casa\231lan: bad owner name (check-names)
/etc/bind/db.casa.lan:18: fluke.casa\231lan: bad owner name (check-names)
zone casa\231lan/IN: loaded serial 20051229
OK


```

---

### Post by extase on 2005-12-29
hi again. 

Sorryh, i had a misconfiguration problem. 

now, i think the zone file is working. Output

```


root@matrix:/etc/bind# named-checkzone home.lan /etc/bind/db.home.lan
zone home.lan/IN: loaded serial 20051229
OK
root@matrix:/etc/bind#


```


The initial problem still remains: 

```


nmap 127.0.0.1

Starting nmap 3.81 ( http://www.insecure.org/nmap/ ) at 2005-12-29 14:26 WET
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1659 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
22/tcp   open  ssh
631/tcp  open  ipp
1026/tcp open  LSA-or-nterm
1027/tcp open  IIS

Nmap finished: 1 IP address (1 host up) scanned in 1.094 seconds
 

```

---

### Post by Koybe on 2005-12-29
Hello,

Are you sure you mentionned /etc/bind/db.home.lan in your zone configuration?

---

### Post by extase on 2005-12-29
what do you mean? 

i will show you my named.conf file:

```


options {
        forwarders { 192.168.0.1; };
        directory "/etc/bind";
        pid-file "named.pid";
        allow-query { any; };
};

acl "home.lan" { 192.168.0.0/24; 127.0.0.1;};

zone "." { type hint; file "db.root"; };

zone "home.lan" {
        type master;
        file "/etc/bind/db.home.lan";
};

zone "0.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.192.168.0";
};


controls {
        inet 127.0.0.1 allow {localhost; } keys { "/etc/bind/rndc.key"; };
};

key "/etc/bind/rndc.key" {
        algorithm hmac-md5;
        secret "my-key";
};


```

and zone file: 

```


$TTL 3h
@               IN              SOA     ns.home.lan.    matrix.home.lan. (
                                                20051229
                                                8H
                                                2H
                                                1W
                                                1D )

@               IN              NS      ns.home.lan.
@               IN              MX      10      mail.home.lan.

ns              IN              A       192.168.0.50
matrix          IN              A       192.168.0.50
mail            IN              A       192.168.0.100
neo             IN              A       192.168.0.100
apoc            IN              A       192.168.0.150
trinity         IN              A       192.168.0.151
fluke           IN              A       192.168.0.152


```

Thanks

---

### Post by Koybe on 2005-12-29
It seems ok. Can you try with this line in your zone file? (just remove "ns.")

```
@               IN              SOA     home.lan.    matrix.home.lan. (
```

And don't forget to restart bind when you make a change ;)

And if it's not working can you do 
```
cat /var/log/syslog | grep named
```

---

### Post by extase on 2005-12-29
Ok: 


I made the changes. But still the same: 

```


Starting nmap 3.81 ( http://www.insecure.org/nmap/ ) at 2005-12-29 15:22 WET
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1659 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
22/tcp   open  ssh
631/tcp  open  ipp
1025/tcp open  NFS-or-IIS
1026/tcp open  LSA-or-nterm

Nmap finished: 1 IP address (1 host up) scanned in 1.273 seconds

root@matrix:/etc/bind# named-checkzone home.lan /etc/bind/db.home.lan
zone home.lan/IN: loaded serial 20051229
OK
root@matrix:/etc/bind# named-checkconf
root@matrix:/etc/bind#


```

---

### Post by Koybe on 2005-12-29
You'd better use  
```
nslookup ns.home.lan
``` for testing. You'll see if it's connecting to the server.

You can also try to regenerate a rndc configfile using. Try it in the /root directory and backup your actual file.
```
rndc-confgen
```

---

### Post by extase on 2006-01-01
Ok. 

named still not working: 

So i ran this command: 

```

cat /var/log/syslog | grep named
Jan  1 07:39:07 localhost named[26010]: There may be a name server already running on [192.168.0.100].53
Jan  1 07:39:07 localhost named[26010]: deleting interface [192.168.0.100].53
Jan  1 07:39:07 localhost named[26010]: not listening on any interfaces
Jan  1 07:39:07 localhost named[26010]: USAGE 1136101147 1134243352 CPU=2.42063u/0.766883s CHILDCPU=0u/0s
Jan  1 07:39:07 localhost named[26010]: NSTATS 1136101147 1134243352
Jan  1 07:39:07 localhost named[26010]: XSTATS 1136101147 1134243352 RR=0 RNXD=0 RFwdR=0 RDupR=0 RFail=0 RFErr=0 RErr=0 RAXFR=0 RLame=0 ROpts=0 SSysQ=0 SAns=0 SFwdQ=0 SDupQ=0 SErr=0 RQ=0 RIQ=0 RFwdQ=0 RDupQ=0 RTCP=0 SFwdR=0 SFail=0 SFErr=0 SNaAns=0 SNXD=0 RUQ=0 RURQ=0 RUXFR=0 RUUpd=0

```


what should i do ? 

:???:

---

### Post by Koybe on 2006-01-13
Hey I was off for a time.

Did you try restarting your rndc configuration with rndc-confgen? I don't exactly know how is it working as i never do that. 

Just have a look ;)

---

### Post by extase on 2006-01-13
hmmm well..

im going to reinstall bind. And if the problem goes on, i cre8 a new post. 

Thanks anyway.

---

### Post by biztux on 2007-05-25
**Here is a little info which might help you:**
**The named.conf file.**

//  /etc/bind/named.conf
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
key "homekey" {
        algorithm hmac-md5;
        secret "my-secret-HMAC-MD5-Encoded";
};

acl "home" { 192.168.100.0/24; 127.0.0.1; };

options {
        directory "/var/cache/bind";
        query-source address * port 53;
        allow-query { "home"; };
        forwarders {
                203.55.158.178;
                203.22.70.2;
                203.22.70.7;
        };
        auth-nxdomain no; # conform to RFC1035
};

controls {
        inet 127.0.0.1 port 953
        allow { 127.0.0.1; 192.168.100.2; } keys { "homekey"; };
};

// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
        type master;
        file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};

// add entries for other zones below here

zone "100.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/homelan.rev";
        allow-update { key homekey; };
};

zone "homelan" {
        type master;
        file "/etc/bind/homelan";
        allow-update { key homekey; };
};

**The rndc.conf file**
/*
 * Copyright (C) 2000, 2001  Internet Software Consortium.
 *
 * Permission to use, copy, modify, and distribute this software for any
 * purpose with or without fee is hereby granted, provided that the above
 * copyright notice and this permission notice appear in all copies.
 *
 * THE SOFTWARE IS PROVIDED "AS IS" AND INTERNET SOFTWARE CONSORTIUM
 * DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL
 * IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL
 * INTERNET SOFTWARE CONSORTIUM BE LIABLE FOR ANY SPECIAL, DIRECT,
 * INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING
 * FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT,
 * NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION
 * WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
 */

/* $Id: rndc.conf,v 1.1 2001/02/13 07:15:34 bdale Exp $ */

/*
 * Sample rndc configuration file.
 */

options {
        default-server  localhost;
        default-key     "homekey";
};

server localhost {
        key     "homekey";
};

/*
*  The  secret "my-secret-HMAC-MD5-Encoded"; must match the one in named.conf.
*/
key "homekey" {
        algorithm hmac-md5;
        secret "my-secret-HMAC-MD5-Encoded";
};

From where you're at it sounds as though you might not have port 53 open in named.conf or named.conf.options.
Often Debian derivatives like UBUNTU "include"  a named.conf.options file instead of  entering the options section in named.conf.

after making the changes, issue the following commands:
pkill named
/etc/init.d/bind9 restart;tail -f /var/log/syslog

You should see the bind9 name server starting up in the syslog (and any errors as well ).

Make sure that /etc/bind has the w bit set for the group and that is is owned by root:bind as follows:
chown root:bind /etc/bind
chmod g+w /etc/bind

This sorts out some silly permissions issues in recent versions of bind9.

I hope this gets you going.

[http://ubuntuforums.org/images/smilies/icon_wink.gif](http://ubuntuforums.org/images/smilies/icon_wink.gif)

---

### Post by andreicimpoca on 2008-05-19
Hi all and let me just say what a wonderful problem this is. I googled this problem and did not find a decent answer for it. I would want to post this answer for anyone interested since this is the first link google sees. If named reports "rndc: 'reload' failed: bad owner name (check-names)" please check the zone file in the chroot jail or wherever you keep the zone file and see names of hosts. In my case they contained an underscore which caused the problem.
Hope this helps someone.
Cheers!
Andrei

---

