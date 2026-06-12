---
title: "sudo rm -Rf /var/lib/dpkg/"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Gustavo Narea on 2007-05-29
Hello.

Yes, I'm a person with Down syndrome and I've ran that silly command, instead of *sudo rm -Rf /var/lib/dpkg/lock*

Now, what should I do? Should I reinstall Kubuntu? Could someone send me the contents of that folder? I use Kubuntu Feisty 32-bit.

Thanks in advance!

---

### Post by mahiyar on 2007-05-29
You must have deleted all the package history and system updates history etc. There will be problem while updating/upgrading, to some extent the damage can be mitigated but not completely see this link [http://www.linuxquestions.org/questions/showthread.php?t=225508](http://www.linuxquestions.org/questions/showthread.php?t=225508)

---

### Post by Gustavo Narea on 2007-05-29
Hi, mahiyar, and thanks for your reply.

It didn't work:

```

gustavo@valencia:~$ sudo dpkg --clear-avail
Password:
dpkg: unable to access dpkg status area for bulk available update: No such file or directory
gustavo@valencia:~$ sudo apt-get update
Get:1 http://kubuntu.org feisty Release.gpg [189B]
Ign http://kubuntu.org feisty/main Translation-en_US
Hit http://kubuntu.org feisty Release
Err http://kubuntu.org feisty Release

Get:2 http://kubuntu.org feisty Release [2887B]
Ign http://kubuntu.org feisty Release
Hit http://kubuntu.org feisty/main Packages
Hit ftp://ftp.mirrorservice.org feisty Release.gpg
Get:3 ftp://ftp.mirrorservice.org feisty/main Translation-en_US
Ign ftp://ftp.mirrorservice.org feisty/main Translation-en_US
Get:4 ftp://ftp.mirrorservice.org feisty/restricted Translation-en_US
Ign ftp://ftp.mirrorservice.org feisty/restricted Translation-en_US
Get:5 ftp://ftp.mirrorservice.org feisty/universe Translation-en_US
Ign ftp://ftp.mirrorservice.org feisty/universe Translation-en_US
Get:6 ftp://ftp.mirrorservice.org feisty/multiverse Translation-en_US
Ign ftp://ftp.mirrorservice.org feisty/multiverse Translation-en_US
Hit ftp://ftp.mirrorservice.org feisty-updates Release.gpg
Get:7 ftp://ftp.mirrorservice.org feisty-updates/main Translation-en_US
Ign ftp://ftp.mirrorservice.org feisty-updates/main Translation-en_US
Get:8 ftp://ftp.mirrorservice.org feisty-updates/restricted Translation-en_US
Ign ftp://ftp.mirrorservice.org feisty-updates/restricted Translation-en_US
Get:9 ftp://ftp.mirrorservice.org feisty-updates/main Translation-en_US
Ign ftp://ftp.mirrorservice.org feisty-updates/main Translation-en_US
Get:10 ftp://ftp.mirrorservice.org feisty-updates/multiverse Translation-en_US
Ign ftp://ftp.mirrorservice.org feisty-updates/multiverse Translation-en_US
Get:11 ftp://ftp.mirrorservice.org feisty-updates/universe Translation-en_US
Ign ftp://ftp.mirrorservice.org feisty-updates/universe Translation-en_US
Hit ftp://ftp.mirrorservice.org feisty-security Release.gpg
Get:12 ftp://ftp.mirrorservice.org feisty-security/main Translation-en_US
Ign ftp://ftp.mirrorservice.org feisty-security/main Translation-en_US
Get:13 ftp://ftp.mirrorservice.org feisty-security/restricted Translation-en_US
Ign ftp://ftp.mirrorservice.org feisty-security/restricted Translation-en_US
Get:14 ftp://ftp.mirrorservice.org feisty-security/universe Translation-en_US
Ign ftp://ftp.mirrorservice.org feisty-security/universe Translation-en_US
Get:15 ftp://ftp.mirrorservice.org feisty-security/multiverse Translation-en_US
Ign ftp://ftp.mirrorservice.org feisty-security/multiverse Translation-en_US
Get:16 ftp://ftp.mirrorservice.org feisty Release [57.2kB]
Get:17 ftp://ftp.mirrorservice.org feisty-updates Release [32.4kB]
Get:18 ftp://ftp.mirrorservice.org feisty-security Release [44.7kB]
Hit ftp://ftp.mirrorservice.org feisty/main Packages
Hit ftp://ftp.mirrorservice.org feisty/restricted Packages
Hit ftp://ftp.mirrorservice.org feisty/universe Packages
Hit ftp://ftp.mirrorservice.org feisty/multiverse Packages
Hit ftp://ftp.mirrorservice.org feisty-updates/main Packages
Hit ftp://ftp.mirrorservice.org feisty-updates/restricted Packages
Hit ftp://ftp.mirrorservice.org feisty-updates/main Packages
Hit ftp://ftp.mirrorservice.org feisty-updates/multiverse Packages
Hit ftp://ftp.mirrorservice.org feisty-updates/universe Packages
Hit ftp://ftp.mirrorservice.org feisty-security/main Packages
Hit ftp://ftp.mirrorservice.org feisty-security/restricted Packages
Hit ftp://ftp.mirrorservice.org feisty-security/universe Packages
Hit ftp://ftp.mirrorservice.org feisty-security/multiverse Packages
Fetched 137kB in 11s (12.1kB/s)
W: GPG error: http://kubuntu.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
E: Could not open lock file /var/lib/dpkg/lock - open (2 No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

---

### Post by taurus on 2007-05-29
Try

```
sudo touch /var/lib/dpkg/lock
sudo aptitude update
sudo aptitude upgrade
```

---

