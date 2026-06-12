---
title: "Apt-get Install Not working"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Darrious on 2006-10-04
I tried to do apt-get install *** and this was the output. 

```

$apt-get install ***
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

I have tried to install other applications too and It gives me the same output.

I looked in the directory that it said to look in and it came up with this.

```
archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_dapper_Release
archive.ubuntu.com_ubuntu_dists_dapper_Release.gpg
archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages
lock
partial
security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_dapper-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_dapper-security_Release
security.ubuntu.com_ubuntu_dists_dapper-security_Release.gpg
security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packagessecurity.ubuntu.com_ubuntu_dists_dapper-security_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_dapper_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_dapper_Release
us.archive.ubuntu.com_ubuntu_dists_dapper_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_dapper_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_dapper-updates_Release
us.archive.ubuntu.com_ubuntu_dists_dapper-updates_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_source_Sources
www.rcpt.to_dists_pending_main_binary-i386_Packages

```

---

### Post by Lord Illidan on 2006-10-04
Can you post your /etc/apt/sources.list here please?

Also, try running ```
sudo apt-get update
```

---

### Post by Darrious on 2006-10-04
When I do ```
apt-get install update
```

It still does the same thing. 

Here is my sources.list

---

### Post by lamego on 2006-10-04
1. If you are new to Ubuntu you should not add extra repositories (except for enabling the universe/multiverse)

2. You are missing the official repositores:

```
# dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
#deb-src http://archive.ubuntu.com/ubuntu dapper main
deb http://archive.ubuntu.com/ubuntu dapper restricted
#deb-src http://archive.ubuntu.com/ubuntu dapper restricted
deb http://archive.ubuntu.com/ubuntu dapper universe
#deb-src http://archive.ubuntu.com/ubuntu dapper universe
deb http://archive.ubuntu.com/ubuntu dapper multiverse
#deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

```

---

### Post by tdrusk on 2006-10-04
I heard that sudo aptitude ___ <program there 
because it works just like synaptic. It makes removal easier or something. I have been trying to get used to typing "aptitude"  instead of "apt-get"

---

### Post by Darrious on 2006-10-04
I'll start to use aptitude now.I forgot to check my sources.list, so after I posted this I had replaced it. I just went to [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic") and just got a new one. Thanks for the help!:mrgreen:

---

### Post by Aelfric5578 on 2006-10-04
Also, make sure you're using "sudo" to run the command.  Because it looks like you're not using it in the console output you've posted, and because the error you're gettong reminds of the one I get when I forget to type sudo (I say it reminds me because I'm not on my Ubuntu PC at the moment to test this)  I'm pretty sure Aptitude won't work either without sudo.

---

### Post by Darrious on 2006-10-05
Also, I wanted to bring something about. What is does sudo really mean.

I always thought it meant like a root command or something.

---

### Post by LookTJ on 2006-10-05
gives you temporary superuser powers

---

