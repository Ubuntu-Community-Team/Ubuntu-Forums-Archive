---
title: "Update manager doesn't work"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by EvilBro on 2007-06-23
I'm pretty new to linux and ubuntu and was pleasantly surprised how little grieve installing ubuntu gave me (namely: none). However, my bliss is beginning to show cracks. The first strange thing is that the login screen sometimes (not always) has a strange resolution (very low). Usually a ctrl-alt-backspace 'solves' this. I suspect it has something to do with the fact that Hsync and Vsync aren't properly specified (although that wouldn't explain the fact that it sometimes does work correctly). This is however a minor issue.

A much bigger issue (for me anyway) is that the update manager (and synaptic) refuses to run properly. It gives the following error:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


How do I fix this?

---

### Post by apjone on 2007-06-23
open a terminal and try 

```

sudo apt-get update -o APT::Cache-Limit=25165824

```

---

### Post by EvilBro on 2007-06-23
That worked. I'll have to read the documentation of apt-get later on to understand what I have actually done, but for now I'm just happy it worked.

Something odd did happen on restart though (I wanted to see if it would still be fixed on the next boot). However I don't see how these things could be related. I got this error:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Message did not receive a reply (timeout by message bus)

GNOME will still try to restart the Settings Daemon next time you log in.


Some icons were weird (as in not the ones I usually have). After selecting 'theme' everything went back to normal again. This is something unrelated, right?

---

### Post by apjone on 2007-06-23
could you open a terminal and do

```

df -h

```

and post the out put here please

---

### Post by EvilBro on 2007-06-23
The output:

```

/dev/hda7             8.7G  3.2G  5.1G  39% /
varrun                633M  100K  633M   1% /var/run
varlock               633M     0  633M   0% /var/lock
procbususb            633M   96K  633M   1% /proc/bus/usb
udev                  633M   96K  633M   1% /dev
devshm                633M     0  633M   0% /dev/shm
lrm                   633M   33M  601M   6% /lib/modules/2.6.20-16-generic/volatile
/dev/hda1              20G   15G  4.7G  77% /media/hda1
/dev/hda5              46G   43G  2.7G  95% /media/hda5

```

---

### Post by chrisbish on 2007-06-23
im having a similar probleme
im a newb to ubuntu.
everything was working until about half an hour ago i can't download anything from the synaptic package manger, add/remove programs or Automatix

i try the code above
> sudo apt-get update -o APT::Cache-Limit=25165824

but all i got was this:

> #####@####-desktop:~$ sudo apt-get update -o APT::Cache-Limit=25165824
Password:

Sorry, try again.
Password:
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by chrisbish on 2007-06-23
any one?

i can't realy do anything with out the codecs.

---

