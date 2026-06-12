---
title: "gdesklets???"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by chef john on 2006-05-16
Hello, I am a newbie to Linux.  have been Windows free for 2 months

I have been trying to tweak breezy badger for an old ibm thinkpad 600e
running on 128mb 4.1 gb hd and 300mhz

I was trying to install the get-apt .... gdesklets and when I input the command in the terminal mode i get the following message...


john@ubuntu:~$ sudo apt-get install gdesklets gdesklets-data
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gdesklets
john@ubuntu:~$

Any ideas as to what may be going on....

Thanks a million

chef john

---

### Post by nalmeth on 2006-05-16
You can install gdesklets thru automatix (see my sig) which will also add it to start-up menu.

OR

Through terminal, give 'er a:
```
sudo apt-get update
apt-cache search gdesklets
``` 
and see what comes up!

---

### Post by jason.b.c on 2006-05-16
I've finally found him, the illusive **Man-bear-pig**.! I'm being totally **Serial**.;)

---

### Post by mostwanted on 2006-05-16
gdesklets is in Universe. You need to enable the Universe repository:

[http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories)

---

### Post by chef john on 2006-05-16
hello nalmeth
tried what you suggested...went through the cycle and got this...
john@ubuntu:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release [30.9kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [60.2kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages [39.0kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources [18.6kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [17.3kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Fetched 199kB in 26s (7649B/s)
Reading package lists... Done
john@ubuntu:~$ apt-cache search gdesklets
john@ubuntu:~$ sudo apt-get install gdesklets gdesklets-data
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gdesklets
john@ubuntu:~$ sudo apt-cache search gdesklets
john@ubuntu:~$ apt-cache search gdesklets

---

### Post by joshrobinson on 2006-05-16
type

```
 sudo gedit /etc/apt/sources.list
```

select everything in the file that opens, delete all the lines, and paste this in its place
```
 # Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```

then 

```
 sudo apt-get update 
```
then try your gdesklets downloads

---

### Post by chef john on 2006-05-16
That did the trick....

Thank-you all for your help

Chef John

---

### Post by joshrobinson on 2006-05-16
[QUOTE=chef john]That did the trick....

Thank-you all for your help

Chef John[/QUOTE]

your welcome :-D

---

