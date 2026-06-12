---
title: "Slimserver install on 7.04 assistance?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Syncstep on 2007-09-26
Hello all,

I just finished installing 7.04 on an old Dell Latitude.  I ran the update after the install, and so far everything runs just fine.  What I am now trying to do is install Slimserver software.  I followed the guidelines on the Slimdevices website:

- I added the following line to sources.list: 

deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main

Here's a copy of my sources.list:
[FONT="Courier New"]
SyncStep-Server-1:/etc/apt$ cat sources.list
deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
[/FONT]

- I successfully ran the following command: 

sudo apt-get update

Then I tried the following command with errors... what the hell am I missing?:

SyncStep-Server-1:/etc/apt$ sudo apt-get install slimserver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  slimserver: Depends: libcgi-perl but it is not installable
              Depends: libclass-accessor-chained-perl but it is not installable
              Depends: libclass-data-inheritable-perl but it is not installable
              Depends: libclass-trigger-perl but it is not installable
              Depends: libclass-virtual-perl but it is not installable
              Depends: libclass-whitehole-perl but it is not installable
              Depends: libcompress-zlib-perl but it is not installable
              Depends: libtimedate-perl but it is not installable
              Depends: libdbd-mysql-perl but it is not installable
              Depends: libdbi-perl but it is not installable
              Depends: libfile-which-perl but it is not installable
              Depends: libgd-gd2-noxpm-perl but it is not installable or
                       libgd-gd2-perl but it is not installable
              Depends: libima-dbi-perl but it is not installable
              Depends: libio-string-perl but it is not installable
              Depends: libio-socket-ssl-perl but it is not installable
              Depends: libnet-dns-perl but it is not going to be installed
              Depends: librpc-xml-perl but it is not installable
              Depends: libfile-slurp-perl but it is not installable
              Depends: libtemplate-perl but it is not installable
              Depends: libdata-page-perl but it is not installable
              Depends: libnet-ip-perl but it is not installable
              Depends: libdigest-sha1-perl but it is not installable
              Depends: libtie-regexphash-perl but it is not installable
              Depends: libpoe-perl but it is not installable
              Depends: libtime-modules-perl but it is not installable
              Depends: libuniversal-moniker-perl but it is not installable
              Depends: libcache-cache-perl but it is not installable
              Depends: libtext-unidecode-perl but it is not installable
              Depends: libtie-cache-perl but it is not installable
              Depends: libcarp-clan-perl but it is not installable
              Depends: liburi-find-perl but it is not installable
              Depends: liberror-perl but it is not installable
              Depends: libclass-singleton-perl but it is not installable
              Depends: libfile-find-rule-perl but it is not installable
              Depends: libxml-writer-perl but it is not installable
              Depends: mysql-server-4.1 but it is not installable or
                       mysql-server-5.0 but it is not installable
              Depends: libmysqlclient14-dev but it is not installable or
                       libmysqlclient15-dev but it is not installable
              Depends: mysql-client-4.1 but it is not installable or
                       mysql-client-5.0 but it is not installable
              Depends: flac but it is not installable
              Depends: sox but it is not installable
E: Broken packages

I thought Perl was part of Ubuntu? I see perl 5.8.8 in the CD manifest.  I also see that I should install the perl, perl-modules and perl-doc packages but apparently, when I try, it says they're installed.  

Any hints here?

Cheers,
S

---

### Post by m9ke on 2007-10-01
Hi Synchstep,

Sorry your slimserver install is being so difficult.  

It looks like you are doing almost exactly the same thing as I did when I installed slimserver.  That install went well and is described in the link below:

[http://ubuntuforums.org/showthread.php?t=555241&highlight=slimserver](http://ubuntuforums.org/showthread.php?t=555241&highlight=slimserver)

The only difference I see between what you describe and what I did was i added the line ```
deb http://debian.slimdevices.com stable main
```
to the end of my /etc/apt/sources.list  

Did you make it the very last line?  I don't know why that might matter, but you might try it.

Also I have all repos enabled universe mulitverse etc.

I am not sure if this will help you, but I hope so.

Cheers,
m9ke

---

