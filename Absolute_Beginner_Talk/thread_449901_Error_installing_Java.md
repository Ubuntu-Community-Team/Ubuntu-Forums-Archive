---
title: "Error installing Java"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by AnthonyRoberson on 2007-05-20
I am trying to install Java.  I am running Kubuntu Feisty Fawn.  I am installing in the Konsole and the install seems to get partially done and then I get the following error:

E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/j/j2se1.4-i586/j2re1.4_1.4.2.02-1ubuntu3_i386.deb:](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/j/j2se1.4-i586/j2re1.4_1.4.2.02-1ubuntu3_i386.deb:) MD5Sum mismatch
E: Unable to correct for unavailable packages
anthony@anthony-desktop:~$

Can anyone help me to resolve this?  I apologize if there is an obvious solution.  I am a complete newb.

---

### Post by taurus on 2007-05-20
Edit /etc/apt/sources.list

```
kdesu kate /etc/apt/sources.list
```
and remove the **us.** from all the repos.  Save it and then run

```
sudo aptitude clean
sudo aptitude update
sudo aptitude install sun-java6-jre sun-java6.plugin sun-java6.font
java -version
```

---

### Post by AnthonyRoberson on 2007-05-20
When I try to run the edit, I get the following error:

anthony@anthony-desktop:~$ gksudo gedit /etc/apt/sources.list
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
anthony@anthony-desktop:~$

---

### Post by taurus on 2007-05-20
If you are running KDE, then you need to use "kdesu kate" instead of "gksudo gedit".

---

### Post by AnthonyRoberson on 2007-05-20
> **taurus said:**
> If you are running KDE, then you need to use "kdesu kate" instead of "gksudo gedit".

Thanks.  I followed the instructions and got the following:

E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-00-2ubuntu2_i386.deb:](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-00-2ubuntu2_i386.deb:) MD5Sum mismatch

anthony@anthony-desktop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
anthony@anthony-desktop:~$  

Not sure if the install worked or not...

---

### Post by taurus on 2007-05-20
Can you post your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

---

### Post by AnthonyRoberson on 2007-05-20
> **taurus said:**
> Can you post your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

Is this it?

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

BTW, thanks SO MUCH for your help.  I am little disappointed with how difficult it has been to install some of the software for Kubuntu, but the help that I have gotten here has been great!!

---

### Post by taurus on 2007-05-20
> **AnthonyRoberson said:**
> Is this it?

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse


That's it!  I think you are missing a bunch of lines above these.  Scroll up and paste the whole file here.

---

### Post by AnthonyRoberson on 2007-05-20
> **taurus said:**
> That's it!  I think you are missing a bunch of lines above these.  Scroll up and paste the whole file here.

DOH!  See.  I told you I was a newb! :)  This should be the whole thing:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
anthony@anthony-desktop:~$

---

### Post by taurus on 2007-05-20
Reboot your machine.  And log back in after it comes back up and run

```
sudo aptitude clean
sudo aptitude update
sudo aptitude install sun-java6-jre sun-java6.plugin sun-java6.font
java -version
```

p.s.  Do you want to install java 1.5 or 1.6?

---

### Post by AnthonyRoberson on 2007-05-20
> **taurus said:**
> Reboot your machine.  And log back in after it comes back up and run

```
sudo aptitude clean
sudo aptitude update
sudo aptitude install sun-java6-jre sun-java6.plugin sun-java6.font
java -version
```

p.s.  Do you want to install java 1.5 or 1.6?

I'm not sure.  Is one preferable over the other?  I am trying to play RuneScape.

---

### Post by taurus on 2007-05-20
Version 1.6 is the latest so may as well install it.

---

### Post by AnthonyRoberson on 2007-05-20
> **taurus said:**
> Version 1.6 is the latest so may as well install it.

Crap.  I am stilling getting an error.  I rebooted and followed the instructions.  I got the following error:

Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse sun-java6-bin 6-00-2ubuntu2 [26.2MB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse sun-java6-jre 6-00-2ubuntu2 [6324kB]
Fetched 32.5MB in 2m1s (269kB/s)
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-00-2ubuntu2_i386.deb:](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-00-2ubuntu2_i386.deb:) MD5Sum mismatch
anthony@anthony-desktop:~$  

What is a MD5Sum mismatch error anyway?

---

### Post by AnthonyRoberson on 2007-05-21
Just a quick bump.  I am still getting the MD5Sum mismatch error when I try to install Java.  Can anyone help?

---

