---
title: "Installing Webmin in Ubuntu Gutsy Gibbon"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Dissident85 on 2008-02-20
I am having a little trouble setting up a LAMP server... every thing has installed fine... well i am up to installed Webmin... i am doing it as per this guide...

[http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html)

but when i try to run this command
```

sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
```

i get this response 

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
perl is already the newest version.
libnet-ssleay-perl is already the newest version.
openssl is already the newest version.
libpam-runtime is already the newest version.
The following NEW packages will be installed:
  libauthen-pam-perl libio-pty-perl libmd5-perl
0 upgraded, 3 newly installed, 0 to remove and 39 not upgraded.
Need to get 42.3kB/80.2kB of archives.
After unpacking 365kB of additional disk space will be used.
Err http://au.archive.ubuntu.com gutsy/universe libio-pty-perl 1:1.07-1
  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/libi/libio-pty-perl/libio-pty-perl_1.07-1_i386.deb  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

Please help :confused::confused::confused:

---

### Post by northern lights on 2008-02-20
Have you followed the hint in the last line of your terminal output?
I.e. ran an update or ran with "--fix-missing"?

---

### Post by Dissident85 on 2008-02-20
> **northern lights said:**
> Have you followed the hint in the last line of your terminal output?
I.e. ran an update or ran with "--fix-missing"?

i ran this

```
 sudo apt-get update --fix-missing
```

still got the same error.

EDIT: i think i used that --fix-missing wrong... 

i just ran
```
sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl --fix-missing
```

it installed the other packages... but still came up with the same error

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
perl is already the newest version.
libnet-ssleay-perl is already the newest version.
openssl is already the newest version.
libauthen-pam-perl is already the newest version.
libpam-runtime is already the newest version.
libmd5-perl is already the newest version.
The following NEW packages will be installed:
  libio-pty-perl
0 upgraded, 1 newly installed, 0 to remove and 39 not upgraded.
Need to get 42.3kB of archives.
After unpacking 168kB of additional disk space will be used.
Err http://au.archive.ubuntu.com gutsy/universe libio-pty-perl 1:1.07-1
  403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/libi/libio-pty-perl/libio-pty-perl_1.07-1_i386.deb  403 Forbidden

```

---

### Post by nfinitone on 2008-02-25
I installed Webmin last night for the first time and I stumbled across your post today. When I downloaded Webmin in the /tmp directory, I ran:

```
sudo dpkg -i webmin_1.400_all.deb
```

After it gave me an error about the missing dependencies, I followed with

```
sudo apt-get -f install
```

apt-get resolved all missing dependencies from there with no problems

---

### Post by Dissident85 on 2008-02-26
fyi: I resolved this issue by download the libio-pty-perl  from this web site [http://packages.debian.org/unstable/perl/libio-pty-perl](http://packages.debian.org/unstable/perl/libio-pty-perl)

---

