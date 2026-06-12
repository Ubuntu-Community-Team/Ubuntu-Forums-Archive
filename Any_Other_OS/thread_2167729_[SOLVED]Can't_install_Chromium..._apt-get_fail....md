---
title: "[SOLVED]Can't install Chromium... apt-get fail..."
date: 2013-08-14
forum: Any Other OS
---

### Post by narutoxela2 on 2013-08-14
Hi everyone, I am trying to install Chromium but when i do "sudo apt-get install Chromium" this is what i get.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 chromium : Depends: libgcrypt11 (>= 1.5.1) but 1.5.0-3ubuntu1 is to be installed
            Depends: libnspr4 (>= 2:4.9-2~) but 4.9.5-0ubuntu0.12.10.1 is to be installed
            Depends: chromium-inspector but it is not going to be installed
 libc6 : Breaks: locales (< 2.17)
 libc6:i386 : Recommends: libc6-i686:i386
              Breaks: locales (< 2.17)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

So, I tried to do "sudo apt-get -f install" and this is what i get... I don't know what to do...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libaudclient2 libid3tag0 libimlib2 libxmmsclient6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  locales
The following packages will be upgraded:
  locales
1 upgraded, 0 newly installed, 0 to remove and 1386 not upgraded.
Need to get 0 B/3,801 kB of archives.
After this operation, 6,394 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  locales
Install these packages without verification [y/N]? y
Preconfiguring packages ...
(Reading database ... 159437 files and directories currently installed.)
Preparing to replace locales 2.13+git20120306-3 (using .../locales_2.17-92_all.deb) ...
Unpacking replacement locales ...
dpkg: error processing /var/cache/apt/archives/locales_2.17-92_all.deb (--unpack):
 trying to overwrite '/usr/sbin/validlocale', which is also in package libc-bin 2.15-0ubuntu20.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.17-92_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by varunendra on 2013-08-15
Welcome to the forums narutoxela2 !

Please try -
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get -f install
```
Post back if there are same or different errors again.

---

### Post by narutoxela2 on 2013-08-15
Alright, so I tried these commands and here is what i get

"sudo apt-get clean": [no output in the command line]

"sudo apt-get autoremove": 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Breaks: locales (< 2.17)
 libc6:i386 : Recommends: libc6-i686:i386
              Breaks: locales (< 2.17)
E: Unmet dependencies. Try using -f.

```

"sudo apt-get -f install": [seems to be the same thing as before]

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libaudclient2 libid3tag0 libimlib2 libxmmsclient6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  locales
The following packages will be upgraded:
  locales
1 upgraded, 0 newly installed, 0 to remove and 1386 not upgraded.
Need to get 3,801 kB of archives.
After this operation, 6,394 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  locales
Install these packages without verification [y/N]? y
Get:1 [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) sid/main locales all 2.17-92 [3,801 kB]
Fetched 3,801 kB in 11s (333 kB/s)                                             
Preconfiguring packages ...
(Reading database ... 159437 files and directories currently installed.)
Preparing to replace locales 2.13+git20120306-3 (using .../locales_2.17-92_all.deb) ...
Unpacking replacement locales ...
dpkg: error processing /var/cache/apt/archives/locales_2.17-92_all.deb (--unpack):
 trying to overwrite '/usr/sbin/validlocale', which is also in package libc-bin 2.15-0ubuntu20.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.17-92_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Thanks for the help!

---

### Post by oldos2er on 2013-08-15
Which version of Ubuntu are you running, and why do you have a debian sid repository enabled?

---

### Post by narutoxela2 on 2013-08-15
I actually have linux mint 14, i figured out that its quite similar to ubuntu so... yeah... I have the sid repository on because i had a problem installing some programs a while back and i guess i enabled it while trying to fix stuff, can it cause troubles?...

---

### Post by oldos2er on 2013-08-15
Thread moved to Other OS/Distro Support.

> can it cause troubles? Yes, it wouldn't surprise me if that's the cause of your current problem.

---

### Post by narutoxela2 on 2013-08-15
Thanks! I removed the sid repository and everything works!

---

### Post by oldos2er on 2013-08-15
Great! You're welcome.

---

