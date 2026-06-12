---
title: "[SOLVED] SAMBA problems HELLLLP"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by maldojr88 on 2007-07-26
hello...well the problem is that i had samba...and deleted my samba.conf file...
so then some dude told me to uninstall and install back agian
so i unistalled using these commands:

$ sudo apt-get clean
$sudo apt-get remove --purge samba

then i typed

$ sudo apt-get install samba 

[B]and i get this:
[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  smbldap-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3341kB of archives.
After unpacking 8184kB of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main samba 3.0.24-2ubuntu1.2 [3341kB]
Fetched 3341kB in 37s (89.9kB/s)                                                
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 120079 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.24-2ubuntu1.2_i386.deb) ...
Setting up samba (3.0.24-2ubuntu1.2) ...
Generating /etc/default/samba...
 * Starting Samba daemons...                                              [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by qpieus on 2007-07-26
hmmm, not sure, but try installing samba-common also. My system has samba and samba-common.


sudo apt-get install samba-common

---

### Post by maldojr88 on 2007-08-01
nope... nothing worked


this is really frustrating

---

### Post by maldojr88 on 2007-08-01
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)



this is the errror i got while doing wat  qpieus said

---

### Post by Greydog on 2007-08-02
So, what was the solution??

I'm having the same problem!

Greydog

---

### Post by pikul on 2007-08-02
> **Greydog said:**
> So, what was the solution??

I'm having the same problem!

Greydog

Try installing it from synaptic :)

---

### Post by maldojr88 on 2007-08-16
i tried but nothing worked

---

