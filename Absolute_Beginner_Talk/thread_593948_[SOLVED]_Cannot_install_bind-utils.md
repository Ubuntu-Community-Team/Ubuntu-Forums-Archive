---
title: "[SOLVED] Cannot install bind-utils"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by chillifire on 2007-10-27
Hi,

I was trying to install the BIND9 utilities (such as dig) on 7.10 with the command

apt-get install bind-utils

But it came back saying that bind-utils was an unkown package. I have installed bind9 and many other packages that way without any problems.

My /etc/apt/sources.list looks like this:


deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy main restricted

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates universe

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

deb [http://download.systemimager.org/debian](http://download.systemimager.org/debian) stable main


Any ideas/suggestions how to install bind-utils or get 'dig and other BIND9 DNS utilities?

Cheers

---

### Post by Maestro23 on 2007-10-27
Try looking for** bind9** in the repo's.

---

### Post by chillifire on 2007-10-27
Thanks for the fast reply.

Unfortunately I cannot decipher it.

What is 'repo's'?

Where would I findr them?

Apologies for what must be daft questions, but I did post in 'Absolute Beginners Forum' with intention :)

Thanks for your help in advance

---

### Post by Maestro23 on 2007-10-27
> **chillifire said:**
> Thanks for the fast reply.

Unfortunately I cannot decipher it.

What is 'repo's'?

Where would I findr them?

Apologies for what must be daft questions, but I did post in 'Absolute Beginners Forum' with intention :)

Thanks for your help in advance

Two ways:

> Gui: System>>Admin>>Synaptic
Search for bind9

Command LIne:

> apt-cache search bind9

---

### Post by chillifire on 2007-10-27
Thanks

running the command on command line gave the following result:

bind9 - Internet Domain Name Server
bind9-doc - Documentation for BIND
bind9-host - Version of 'host' bundled with BIND 9.X
libbind9-30 - BIND9 Shared Library used by BIND
bindgraph - DNS statistics RRDtool frontend for BIND9
gbindadmin - GTK+ configuration tool for bind9
gforge-dns-bind9 - collaborative development tool - DNS management (using Bind9)
host - utility for querying DNS servers
libconfig-auto-perl - Magical config file parser
libnss-lwres - NSS module for using bind9's lwres as a naming service
libbind9-0 - BIND9 Shared Library used by BIND

I ran also 

apt-get search bind

which gave me a huge list of stuff, but no bind-utils. I tried and installed bind9-host for good measure (description sounded promissing). Still, the dig command is still unnkown.

If the answer is bindutils package does not exist for debian or ubuntu, so be it. 'dig' seems to be such a common tool though to analyse DNS, that I need to keep asking: Where can I get it? can it be downloaded as a tar-ball somewhere?

Cheers

---

### Post by Maestro23 on 2007-10-27
Quick google of Bind-Utils found:

[http://linux.maruhn.com/sec/bind-utils.html](http://linux.maruhn.com/sec/bind-utils.html)

Those are .rpm packages, so you will have to use the "ailen" command to install.

Following link will help with installing software:
[http://www.psychocats.net/ubuntu/installingsoftware#rpm](http://www.psychocats.net/ubuntu/installingsoftware#rpm)


There might be other download sites out there, just google.

Good luck man.

---

### Post by chillifire on 2007-10-27
Thanks that was very helpful.

downloaded the rpm package with wget and installed with alien command.

Unfortunately, the alien install aborts - it sounds to me like a dependency that cannot be resolved:

root@finch:/tmp# alien -i bind-utils-9.4.0-6.fc7.i386.rpm
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: bind-utils-9.4.0-6.fc7.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
        dpkg --no-force-overwrite -i bind-utils_9.4.0-7_i386.deb
Selecting previously deselected package bind-utils.
(Reading database ... 26627 files and directories currently installed.)
Unpacking bind-utils (from bind-utils_9.4.0-7_i386.deb) ...
dpkg: error processing bind-utils_9.4.0-7_i386.deb (--install):
 trying to overwrite `/usr/bin/host', which is also in package bind9-host
Errors were encountered while processing:
 bind-utils_9.4.0-7_i386.deb
Unable to install at /usr/share/perl5/Alien/Package/Deb.pm line 92.
        find bind-utils-9.4.0 -type d -exec chmod 755 {} ;
        rm -rf bind-utils-9.4.0

So here I am again, how does a mere mortal install utilities like dig, dnsquery, nslookup on Ubuntu?

Cheers

---

### Post by chillifire on 2007-10-27
I found my own solution:

It is called apt-file and it can search for a file in any package (installed or not). 

$ sudo apt-get install apt-file

$ sudo apt-file update

$ apt-file search autoexpect

This way I found nslookup was in package dnsutils.

$ sudo apt-get install dnsutils

gave me dig, nslookup etc.


**Thanks Maestro23 for sticking with me and putting me on the right track.**:KS

---

### Post by Maestro23 on 2007-10-27
> **chillifire said:**
> I found my own solution:

It is called apt-file and it can search for a file in any package (installed or not). 

$ sudo apt-get install apt-file

$ sudo apt-file update

$ apt-file search autoexpect

This way I found nslookup was in package dnsutils.

$ sudo apt-get install dnsutils

gave me dig, nslookup etc.


**Thanks Maestro23 for sticking with me and putting me on the right track.**:KS

Good deal man.  Never had cause to use the Bind9 stuff myself.  Glad I at least put you on the right track. :)

Don't forget to mark this SOLVED via the Thread Tools.

---

