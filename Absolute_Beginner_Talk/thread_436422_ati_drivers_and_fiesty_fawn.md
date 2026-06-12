---
title: "ati drivers and fiesty fawn"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by simplekin on 2007-05-07
I have just downloaded ATI drivers for my all in wonder x800 video card, and once i installed, it was actually x64 when I actually asked for a normal x86. How can I install the proper way a video driver for my card?

---

### Post by machoo02 on 2007-05-07
The binary FGLRX driver is already in the repositories, so you are simply a ```
sudo aptitude install xorg-driver-fglrx
```away!

For a little more detailed how-to, check out [this site]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide").

---

### Post by simplekin on 2007-05-08
ok it gave me a bunch of errors


crunchystrike@crunchystrike:~$ sudo aptitude install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up amavisd-new (2.4.2-6) ...
Creating/updating amavis user account...
Starting amavisd:   The value of variable $myhostname is "crunchystrike", but should have been
  a fully qualified domain name; perhaps uname(3) did not provide such.
  You must explicitly assign a FQDN of this host to variable $myhostname
  in amavisd.conf, or fix what uname(3) provides as a host's network name!
(failed).
invoke-rc.d: initscript amavis, action "start" failed.
dpkg: error processing amavisd-new (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of amavisd-new-milter:
 amavisd-new-milter depends on amavisd-new (= 1:2.4.2-6); however:
  Package amavisd-new is not configured yet.
dpkg: error processing amavisd-new-milter (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amavisd-new
 amavisd-new-milter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up amavisd-new (2.4.2-6) ...
Creating/updating amavis user account...
Starting amavisd:   The value of variable $myhostname is "crunchystrike", but should have been
  a fully qualified domain name; perhaps uname(3) did not provide such.
  You must explicitly assign a FQDN of this host to variable $myhostname
  in amavisd.conf, or fix what uname(3) provides as a host's network name!
(failed).
invoke-rc.d: initscript amavis, action "start" failed.
dpkg: error processing amavisd-new (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of amavisd-new-milter:
 amavisd-new-milter depends on amavisd-new (= 1:2.4.2-6); however:
  Package amavisd-new is not configured yet.
dpkg: error processing amavisd-new-milter (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amavisd-new
 amavisd-new-milter
crunchystrike@crunchystrike:~$ 


yeah, kinda in a problem here

---

### Post by jespdj on 2007-05-08
> 
crunchystrike@crunchystrike:~$ sudo aptitude install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

So, you already have fglrx installed.

> 
Setting up amavisd-new (2.4.2-6) ...
Creating/updating amavis user account...
Starting amavisd: The value of variable $myhostname is "crunchystrike", but should have been
a fully qualified domain name; perhaps uname(3) did not provide such.
You must explicitly assign a FQDN of this host to variable $myhostname
in amavisd.conf, or fix what uname(3) provides as a host's network name!
(failed).

I have no idea what "amavisd" is and why it is trying to install this, but pay attention to the error message.

Ok, I found [this](http://www.ijs.si/software/amavisd/) with Google. It looks like some kind of anti-virus program, I don't think this has anything to do with your graphics driver.

---

