---
title: "Install SSH Server and Configure Problem"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2007-03-30
Hello. I have setup an ubuntu 6.10 box which I want to set up as Web/FTP/SSH Server.

I am fairly new to Linux, so I experience quite a few difficulties.

I looked up the Ubuntu:Edgy Guide: HOWTO install the SSH Server.
I did as follows:

         sudo apt-get install ssh


However, I got the following result:

ahlandberg@ubuntu610:~$ sudo apt-get install ssh
Password:
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
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ssh: Depends: openssh-server but it is not going to be installed
E: Broken packages




My idea is to setup the SSH Server so that I can use WinSCP to logon to the ubuntu machine from my other Windows computers on the LAN and later also from the Internet through a DynDns address.


I appreciate any kind of help!!!

Anders

---

### Post by Coinnach on 2007-03-30
Hi Anders try 'sudo apt-get install ssh openssh-server' and see if it installs at that point

---

### Post by albesan on 2007-03-30
Hey there,
Have you got all the repositories enabled?
Have you tried using synaptic and trying to do a search for the name openssh and installing using this method?

hope this helps.


a.

---

### Post by ahlandberg on 2007-03-30
> **albesan said:**
> Hey there,
Have you got all the repositories enabled?
Have you tried using synaptic and trying to do a search for the name openssh and installing using this method?

hope this helps.


a.


1. Which repositories do you mean? My /etc/apt/sources.list file contains:


## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 



This is the sources.list file that is listed on the Ubuntu Edgy Guide.

2. What is synaptic??

---

### Post by ahlandberg on 2007-03-30
> **Coinnach said:**
> Hi Anders try 'sudo apt-get install ssh openssh-server' and see if it installs at that point

Hi! I tried to execute that command but again, I get this error:



ahlandberg@ubuntu610:~$ sudo apt-get install ssh openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openssh-server: Depends: openssh-client (= 1:4.1p1-7ubuntu4.2) but 1:4.3p2-5ubuntu1 is to be installed
E: Broken packages




Also, when I try to install eclipse using 


sudo aptitude install eclipse


I also get these kind of messages and it doesn't install.

---

### Post by rich.bradshaw on 2007-03-30
try 

sudo apt-get update

sudo aptitude install ssh openssh-server

aptitude sometimes is more helpful and can find out how to resolve dependancies.

---

### Post by Coinnach on 2007-03-30
Anders, have a look at this link - it will show you how to use Synaptic. Try installing SSH and Openssh Server from there.

[http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)

---

### Post by ahlandberg on 2007-03-30
Hi people.

Alright, I changed the sources to my ubuntu distribution (edgy) and was able to do all the updates.

When I search for SSH server or OpenSSH Server in the Synaptic, I cannot find it - only the SSH Client.

Further, when I run the install command from the prompt, I get this:



ahlandberg@ubuntu610:~$ sudo aptitude install ssh openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for ssh
No candidate version found for openssh-server
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done



In the Synaptic, I have all internet sources ticked, however, no sources in the Third Party section.

Does somebody have an idea what I am doing wrong/ what I need to do?

Thanks so much!

Anders

---

### Post by Coinnach on 2007-03-30
Did you search for openssh-server in synaptic?

---

### Post by pruhnke on 2007-03-30
I just installed Open SSH on my Xubuntu 6.06 box today.  I found it in synaptic, but from the command line this is all you should need.

```
sudo apt-get install openssh-server
```

apt-get should resolve the dependancy for openssh-client (the server requires the client), if not I would try installing it first.

```
sudo apt-get install openssh-client
sudo apt-get install openssh-server
```

Good luck!

---

