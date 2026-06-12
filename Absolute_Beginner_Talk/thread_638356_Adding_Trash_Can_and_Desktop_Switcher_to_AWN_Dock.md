---
title: "Adding Trash Can and Desktop Switcher to AWN Dock"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-12-11
I would like to put the Desktop switch and the Trash Can
on my AWN Dock, how do I do this?  I looked in the 
AWN preferences and I don't see anything I can do.
Under applets there is only 1 idem listed and when
I choose add it just list all my folders in my home
directory......

---

### Post by subs on 2007-12-12
> **Orbital75 said:**
> I would like to put the Desktop switch and the Trash Can
on my AWN Dock, how do I do this?  I looked in the 
AWN preferences and I don't see anything I can do.
Under applets there is only 1 idem listed and when
I choose add it just list all my folders in my home
directory......


System > Preferences > AWN Manager > Applets

now from the right most pane select "Trash Applet" and "Launcher/Task Manager"

then click the button which shows a left arrow (<=) and refresh the awn dock

---

### Post by Orbital75 on 2007-12-12
Thanks for your help but it seems the only thing
I have in the applets tab is Launch/Task Manager
There are no other Applets in the columns. Do
I need to add applets or something? I have no
idea how.  I searched in the repository but nothing
came up.

---

### Post by atomkarinca on 2007-12-12
I guess the thing you need is

```
sudo apt-get install awn-core-applets
```

or if you installed AWN using the guide on this forums,

```
sudo apt-get install awn-core-applets-bzr
```

then you should get a bunch of applets in the applets tab.

---

### Post by Orbital75 on 2007-12-12
All I did was went into the repositories search for and installed
Avant Window Navigator.  Which of those options posted should I use?
Thank you. :)

---

### Post by atomkarinca on 2007-12-12
Add these to your /etc/apt/sources.list:

```
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

then try

```
sudo apt-get install awn-core-applets
```

---

### Post by Orbital75 on 2007-12-12
I got this when I tried to install the 3rd party repository.

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181

Still tried it though after it place it in the repository and got this.
MyComputer@Orbital:~$ sudo apt-get install awn-core-applets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package awn-core-applets
MyComputer@Orbital:~$

I tried then to just search in the Synaptic package Manager and found this
awn-core-applets-bzr

When I get ready to install it, it warns me that it can't be authenticated
and there counld be a chance its something bad that could take over
my Computer.  Sorry I'm a newbie and learning.

---

### Post by CarpKing on 2007-12-12
Try "sudo apt-get install awn-core-applets-bzr"

---

### Post by subs on 2007-12-13
> **Orbital75 said:**
> I got this when I tried to install the 3rd party repository.

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181

Still tried it though after it place it in the repository and got this.
MyComputer@Orbital:~$ sudo apt-get install awn-core-applets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package awn-core-applets
MyComputer@Orbital:~$

I tried then to just search in the Synaptic package Manager and found this
awn-core-applets-bzr

When I get ready to install it, it warns me that it can't be authenticated
and there counld be a chance its something bad that could take over
my Computer.  Sorry I'm a newbie and learning.


just go ahead with it

---

### Post by Orbital75 on 2007-12-13
thanks

---

### Post by Orbital75 on 2007-12-13
I ran it now this happens...... something didn't seem to install right.

[IMG]http://img177.imageshack.us/img177/8330/screenshotcp1.png[/IMG]


I did what it said and I get this.

Orbital75@Orbital:~$ sudo apt-get install -f
[sudo] password for orbital75:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgnome-compiz-manager0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libawn-bzr python-libawn-bzr
The following NEW packages will be installed:
  libawn-bzr python-libawn-bzr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/90.9kB of archives.
After unpacking 283kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libawn-bzr python-libawn-bzr
Install these packages without verification [y/N]? y
(Reading database ... 97799 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.2.0-bzr151-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr151-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package avant-window-navigator
Unpacking python-libawn-bzr (from .../python-libawn-bzr_0.2.0-bzr151-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr151-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.5/site-packages/awn/awn.so', which is also in package avant-window-navigator
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr151-1_i386.deb
 /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr151-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Orbital75@Orbital:~$

---

### Post by Orbital75 on 2007-12-13
I just would like to let everyone that I fix the problem by completely
removing awn-core-applets-bzr using the Synaptic Package
Manager..... I'm not sure what caused this but removing it seem
to have fixed the issue.  I honestly think something just didn't
install right or it had some dependency I couldn't meet.
It did state some form of error when it first installed.

---

### Post by mathnerd314 on 2007-12-29
> **CarpKing said:**
> Try "sudo apt-get install awn-core-applets-bzr"

I tried both "sudo apt-get install awn-core-applets" and "sudo-apt-get install awn-core-applets-bzr" but got the error "E: Couldn't find package awn-core-applets".

I installed the .deb file from getdeb.net - maybe that's why?

---

### Post by Jake90 on 2008-01-21
> **mathnerd314 said:**
> I tried both "sudo apt-get install awn-core-applets" and "sudo-apt-get install awn-core-applets-bzr" but got the error "E: Couldn't find package awn-core-applets".

I installed the .deb file from getdeb.net - maybe that's why?
Try switching awn-core-applets to awn-extras

---

