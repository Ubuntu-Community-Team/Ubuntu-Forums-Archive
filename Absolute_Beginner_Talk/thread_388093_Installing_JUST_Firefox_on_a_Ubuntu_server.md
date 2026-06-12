---
title: "Installing JUST Firefox on a Ubuntu server?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by rlwpub on 2007-03-19
I have a Ubuntu server with LAMP installed on an old P2 233 computer. It is working fine.

What I want to do is install JUST Firefox on it. No other graphical applications.

What are the minimum packages that need to be installed to get Firefox working on a LAMP server install?

Thanks for any and all help in advance.

Re's
Rob

---

### Post by giftnudel on 2007-03-19
Hi,

I think you only need the xinit package, the xserver-xorg-video-* package matching your hardware and firefox (+any additional packages they depend on)

You should then be able to run 
```
xinit firefox
```

and it should work (if you configured your xserver accordingly)

I have not tested that, but I am quite certain that's very close to the minimum you need.

giftnudel

---

### Post by rlwpub on 2007-03-19
> **giftnudel said:**
> Hi,

I think you only need the xinit package, the xserver-xorg-video-* package matching your hardware and firefox (+any additional packages they depend on)

You should then be able to run 
```
xinit firefox
```

and it should work (if you configured your xserver accordingly)

I have not tested that, but I am quite certain that's very close to the minimum you need.

giftnudel

I get a can't find xinit and that it has been replaced with x11-common.

I installed x11-common and firefox. Firefox will still not run. get the following error.

/opt/firefox/firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

Re's
Rob

---

### Post by rlwpub on 2007-03-19
I'm a noob to this. Do I need to install xserver first? And if so, how do I install xserver on a Ubuntu server LAMP install?

Re's
Rob

---

### Post by mahy on 2007-03-19
> **rlwpub said:**
> I get a can't find xinit and that it has been replaced with x11-common.

I installed x11-common and firefox. Firefox will still not run. get the following error.

/opt/firefox/firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

Re's
Rob

It seems you need libgtk-x11 as well. Well, install it then! However, chances are another problem will surface...

---

### Post by butlershouse on 2007-03-19
Hello rlwpub out of interest ( and purely in a neutral tone ) what are you hoping to achieve in having firefox directly on the server. I would suggest if your trying to install a package without ending up in dependency hell then you should install from binaries delivered by Mozilla directly. This way you will have the whole Firefox package installed in a directory and your apt packages list wont be tainted with a package that might flag a future need for upgrades and X installs.

---

### Post by rlwpub on 2007-03-19
> **butlershouse said:**
> Hello rlwpub out of interest ( and purely in a neutral tone ) what are you hoping to achieve in having firefox directly on the server. I would suggest if your trying to install a package without ending up in dependency hell then you should install from binaries delivered by Mozilla directly. This way you will have the whole Firefox package installed in a directory and your apt packages list wont be tainted with a package that might flag a future need for upgrades and X installs.

I downloaded the binaries for firefox and installed. When I try to run it by typing firefox at the command line I get....

/opt/firefox/firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

What I am trying to do is this.

I am setting up a check-in computer. The check-in program is written in PHP and uses mySQL. It is browser driven.

Re's
Rob

---

### Post by rlwpub on 2007-03-19
> **mahy said:**
> It seems you need libgtk-x11 as well. Well, install it then! However, chances are another problem will surface...

This is what I get...

sudo apt-get install libgtk-x11
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libgtk-x11

What am I doing wrong?

Re's
Rob

---

### Post by rlwpub on 2007-03-19
Basically what I am trying to do is setup a computer that ONLY has the following.

Linux
mySQL
PHP
Apache
Firefox

Re's
Rob

---

### Post by rlwpub on 2007-03-19
Also how do you set the initial root mysql password on a new LAMP install?

Re's
Rob

---

### Post by tom56 on 2007-03-19
Firefox has a lot of graphical dependencies. If it's a web browser you want install links. It has a graphical mode, but won't insist install GNOME and a bunch of other stuff.

sudo aptitude install links2

then run it with

links2 -g [www.google.com](www.google.com)

(the -g stands for graphical mode)

---

### Post by tom56 on 2007-03-19
> **butlershouse said:**
> Hello rlwpub out of interest ( and purely in a neutral tone ) what are you hoping to achieve in having firefox directly on the server. I would suggest if your trying to install a package without ending up in dependency hell then you should install from binaries delivered by Mozilla directly. This way you will have the whole Firefox package installed in a directory and your apt packages list wont be tainted with a package that might flag a future need for upgrades and X installs.

This won't work because these binaries have just the same dependencies as apt-get but they won't be installed automatically for you.

---

### Post by justleen on 2007-03-19
EDIT:  Giftnudel is very much right! corrected my post to reflect this

not sure about your firefox, to be honest, since you installed a LAMP.. I would just try to install the missing deps. Have you tried somdething like

```
 sudo apt-get install firefox 
```


you can set the root passwd for mysql with 
```
 mysqladmin -u root password "newpasswd" 
```

see also
[http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html](http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html)

---

### Post by giftnudel on 2007-03-19
```
sudo apt-get install firefox
``` will install everything you need to get it running. You need that and exactly that.
```
sudo apt-get build-dep firefox
``` will install the **build** depends on firefox, you only need that when you wnat to compile the software on your own.
So again if you want firefox, run ```
sudo apt-get install firefox
```

giftnudel

---

### Post by rlwpub on 2007-03-20
> **tom56 said:**
> Firefox has a lot of graphical dependencies. If it's a web browser you want install links. It has a graphical mode, but won't insist install GNOME and a bunch of other stuff.

sudo aptitude install links2

then run it with

links2 -g [www.google.com](www.google.com)

(the -g stands for graphical mode)

I'll be happy with any browser as long as it handles forms. When I ran the sudo aptitude install links2 I get...

Couldn't find any package whose name or description matched "links2"

Re's
Rob

---

### Post by tom56 on 2007-03-20
Yes, links2 can handle forms.

Have you enabled the universe repo? Make sure the following lines are in your /etc/apt/sources.list (uncommented, obviously - and including multiverse and universe)

```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

```

Obviously edgy needs to be whatever version you're running (e.g., dapper, feisty). You can find out more about repositories and sources.list here - [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

Should install once you've added universe.

---

### Post by rlwpub on 2007-03-21
> **tom56 said:**
> Yes, links2 can handle forms.

Have you enabled the universe repo? Make sure the following lines are in your /etc/apt/sources.list (uncommented, obviously - and including multiverse and universe)

```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

```

Obviously edgy needs to be whatever version you're running (e.g., dapper, feisty). You can find out more about repositories and sources.list here - [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

Should install once you've added universe.

Added those lines and changed to dapper. Then ran...

sudo apt-get update

Then ran

sudo aptitude install links2

Then got

Couldn't find any package whose name or description matched "links2"

Re's
Rob

---

### Post by cowlip on 2007-03-21
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=links2&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=links2&searchon=names&subword=1&version=all&release=all)

It should be there, have you tried to download a deb from this website otherwise then?  Pick the one that your version of ubuntu is.  If it needs dependancies then do "sudo apt-get -f install" and they should install

giftnudel's advice is also good

---

### Post by rlwpub on 2007-03-21
> **cowlip said:**
> [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=links2&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=links2&searchon=names&subword=1&version=all&release=all)

It should be there, have you tried to download a deb from this website otherwise then?  Pick the one that your version of ubuntu is.  If it needs dependancies then do "sudo apt-get -f install" and they should install

giftnudel's advice is also good

I must not know anything. :( I tried that and this is what I get....

sudo dpkg -i links2.deb
Selecting previously deselected package links2.
(Reading database ... 16419 files and directories currently installed.)
Unpacking links2 (from links2.deb) ...
dpkg: dependency problems prevent configuration of links2:
 links2 depends on libdirectfb-0.9-22; however:
  Package libdirectfb-0.9-22 is not installed.
 links2 depends on libsvga1; however:
  Package libsvga1 is not installed.
dpkg: error processing links2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 links2

There has to be an easier way.

Re's
Rob

---

### Post by seshomaru samma on 2007-03-21
links2 has a lot of dependencies (see [here]("http://packages.debian.org/unstable/net/links2"))
if you install it with apt , apt will solve the dependencies for you
it is definitely in the universe repos (see [here]("http://packages.ubuntulinux.org/edgy/net/"))
but you say that you added the repos and it apt says it cannot find the package , very strange
can you post the output of 
```
sudo apt-get update
```

---

### Post by tom56 on 2007-03-21
And post your /etc/apt/sources.list please

---

### Post by rlwpub on 2007-03-22
Here is my sources.list file.

#
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restr$


deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restric$

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multive$


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

When I run apt-get update does it write to a file? If so, what file and I'll post that also.

Re's
Rob

---

### Post by seshomaru samma on 2007-03-22
when you run apt-get update you get a lot of input in the terminal , copy that and paste it into a text file . to do that open the gedit text-editor br running:
```
gedit name_of_file
```
if for some reason ,you dont have gedit installed use nano (the same way)

---

### Post by rlwpub on 2007-03-22
Here is the apt-get update output.

sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages [2458kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [50.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [102kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages [2458kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [7250B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [20.1kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [983B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [53.1kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [6729B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [102kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [7250B]
16% [15 Packages bzip2 0] [9 Packages 107865/2458kB 4%] [16 Packages 5383/7250B 74%] [4 Packagesbzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Sub-process bzip2 returned an error code (2)
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [53.1kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [4082B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [20.1kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [983B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [6729B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources [771B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages [3225kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages [3225kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection timed out [IP: 91.189.89.8 80]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [172kB]
12% [25 Packages gzip 0] [24 Packages 772707/3225kB 23%]                38.2kB/s 49710d 6h23m39s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Sub-process gzip returned an error code (1)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  Connection timed out [IP: 91.189.89.8 80]
Fetched 334kB in 4m34s (1216B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Connection timed out [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Connection timed out [IP: 91.189.89.8 80]
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Re's
Rob

---

### Post by seshomaru samma on 2007-03-22
I'm by no means an apt expert
but I can see the update didn't work. 
Looking at your sources list - I can see that you have two sets of the same sources- the default repos and the US mirrors on the same list ,this is why you got this error:
```
W: Duplicate sources.list entry
```
What I would do is open the sources list again (sudo gedit /etc/apt/sources.list) and comment out all the repos that do not have 'us' in their address ,therby leaving only the US mirrors(just add a # to the line). Then run apt-get update. If this doesn't work. go to [this website ]("http://www.ubuntu-nl.org/source-o-matic/"), generate a new sources.list and try apt-get update.
If all this doesn't work and you still get errors -then you have an apt problem . I would suggest starting a new thread posting all the errors you've got, smarter people than me would be able to help you.
Good luck.

---

### Post by rlwpub on 2007-03-22
> **seshomaru samma said:**
> I'm by no means an apt expert
but I can see the update didn't work. 
Looking at your sources list - I can see that you have two sets of the same sources- the default repos and the US mirrors on the same list ,this is why you got this error:
```
W: Duplicate sources.list entry
```
What I would do is open the sources list again (sudo gedit /etc/apt/sources.list) and comment out all the repos that do not have 'us' in their address ,therby leaving only the US mirrors(just add a # to the line). Then run apt-get update. If this doesn't work. go to [this website ]("http://www.ubuntu-nl.org/source-o-matic/"), generate a new sources.list and try apt-get update.
If all this doesn't work and you still get errors -then you have an apt problem . I would suggest starting a new thread posting all the errors you've got, smarter people than me would be able to help you.
Good luck.

I tried it without the duplicate sources. Still the same problem. Just added the additional sources per messages here to see if that helped.

Re's
Rob

---

### Post by seshomaru samma on 2007-03-22
> **rlwpub said:**
> I tried it without the duplicate sources. Still the same problem. Just added the additional sources per messages here to see if that helped.

Re's
Rob

not sure i understand.did you try replacing your whole sourcs list with the one generated by the link i gave you?

---

### Post by tom56 on 2007-03-22
Delete everything in your /etc/apt/sources.list and replace it with the following. It's exactly what you had before but tidied up a bit and with duplicates removed. I've assumed you're in the U.S. for the mirrors.

```
# Main repos
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

# Security updates
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

# Updates
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

# Backports (commented out for now)
#deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
```

---

### Post by rlwpub on 2007-03-23
tom56,

I replaced it with what you listed. Here is the output from apt-get update.

rob@usacaf:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [102kB]
99% [4 Packages bzip2 0] [Waiting for headers] [Waiting for headers]                 14.0kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages [2458kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages [95.2kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages [21.8kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages [1805B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Sources [3530B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Sources [733B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages [3225kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  Connection timed out [IP: 91.189.89.8 80]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages [121kB]
6% [13 Packages gzip 0]                                                   389kB/s 49710d 6h28m2s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Fetched 159kB in 6m50s (387B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Connection timed out [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
rob@usacaf:~$


I then tried to install links2 and this is what I get.

rob@usacaf:~$ sudo apt-get install links2
Reading package lists... Done
Building dependency tree... Done
Package links2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package links2 has no installation candidate

Re's
Rob

---

### Post by mahy on 2007-03-23
There are no security updates for Dapper universe and multiverse packages. Fix it with changing the appropriate lines to:

# Security updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

**_EDIT: sorry, that's wrong. Out of ideas..._**

---

### Post by rlwpub on 2007-03-23
I'm starting to think it may be better to just install the desktop from CD and then install Apache, mySQL and PHP.

Re's
Rob

---

### Post by mahy on 2007-03-23
> **rlwpub said:**
> I'm starting to think it may be better to just install the desktop from CD and then install Apache, mySQL and PHP.

Re's
Rob

Good point, but that repository problem is still bugging me. Anyway, i'd recommend using Opera in kiosk mode.

---

### Post by Bachstelze on 2007-03-23
Try this :

```

sudo -i
mv /etc/apt/sources.list /etc/apt/sources.list.old
touch /etc/apt/sources.list
apt-get update
mv /etc/apt/sources.list.old /etc/apt/sources.list
```

Then run *apt-get update* again and tell me if you get the same errors.

---

### Post by rlwpub on 2007-03-27
I want to thank everyone for the help I received. What I ended up doing is installing the desktop and then installing Apache, PHP and mySQL.

Now I am going to start taking off all the apps not needed.

Re's
Rob

---

