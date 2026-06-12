---
title: "Installing .bin Files"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Alien260 on 2006-07-19
hello,

i have been using Ubuntu from 4 days now and read all the link 200 people sent reading evenrything, i still dont understand how to install things manually i understood the whole concept of add/remove and synaptic etc.. 

i have to install a file called jre-1_5_0_07-linux-i586.bin 

i try finding it through the terminal but nothing happends. 

another thing i found hunting round the net is this automatix it looks like its a good thing to install on your PC to get the system running well i tried to follow the instructions there but still had no succsess 

can anyone give me a hand, imagine you are talking to a baby.. 

thanks

---

### Post by madmetal on 2006-07-19
for manual installing i hope this helps [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by Jagot on 2006-07-19
If that's the Sun Java JRE you're installing there then you are aware it is is available in the repos?  You need to enable the multiverse repo, then:

```
sudo aptitude update && sudo aptitude install sun-java5-bin
```

---

### Post by Alien260 on 2006-07-19
> **Jagot said:**
> If that's the Sun Java JRE you're installing there then you are aware it is is available in the repos?  You need to enable the multiverse repo, then:

```
sudo aptitude update && sudo aptitude install sun-java5-bin
```

i have my Repos available (all of them)

when i write what you told me in the terminal i get this message 

alien@alien:~$ sudo aptitude update && sudo aptitude install sun-java5-bin
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 4B in 3s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "sun-java5-bin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


why does it not install it??

thanks

---

### Post by FredB on 2006-07-19
To activate extra repositories (universe and multiverse ones) :

Applications Menu - Add / Remove.

Check both "show..." checkboxes. Click on apply then validate.

And more repositories will be added. And you can install Java flawlessly !

---

### Post by Alien260 on 2006-07-19
> **FredB said:**
> To activate extra repositories (universe and multiverse ones) :

Applications Menu - Add / Remove.

Check both "show..." checkboxes. Click on apply then validate.

And more repositories will be added. And you can install Java flawlessly !

i already have both of them ticked. and i still get the same error. 

why does it not install it? 

thanks

---

### Post by bluenova on 2006-07-19
It looks like it's only using universe and not multiverse which is where you will find sun java. I would suggest doing:
```
sudo gedit /etc/apt/sources.list
```
And replace it with the source list [here](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by 3rdalbum on 2006-07-19
> **bluenova said:**
> It looks like it's only using universe and not multiverse which is where you will find sun java. I would suggest doing:
```
gksudo gedit /etc/apt/sources.list
```
And replace it with the source list [here](http://www.ubuntuforums.org/showthread.php?t=185758)

Code fixed.

---

