---
title: "Problems with Installing new packages"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by todaymylove on 2006-12-29
Hello everybody. This morning I just installed the newest verision of ubuntu after I had spent about a week using the LiveCD version to test it out. While using the LiveCD version I was able to use the Add/Remove option to install a bunch of programs that come bundled with ubuntu. I installed aMSN messenger and the VLC media player and they worked just fine.

Well starting today after I decided to install the full operating system I figured I would go ahead and install some of the apps i used on the LiveCD version. However when I try to install aMSN messenger and VLC i get an error saying:

> 
Cannot install 'vlc'

This application conflicts with other installed software. To install 'vlc' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.


I never had this problem before using LiveCD so I went ahead and searched the forums to see if anyone else had this problem when installing packages. I found out how to use this so called "advanced mode" yet I still have the same problems:

> 
alex@alex-laptop:~$ sudo apt-get install amsn
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
  amsn: Depends: imlib11 but it is not going to be installed
        Depends: tcl8.4 but it is not installable
        Depends: sox but it is not going to be installed
        Depends: tk8.4 but it is not installable
        Depends: tcltls but it is not going to be installed
E: Broken packages
alex@alex-laptop:~$ 


This was the general output after using the synaptic package manager as well. 

So anyways, I have no idea whats going on. I never got these problems using the LiveCD version and now all of a sudden??? My installation is fresh - I haven't really done anything with my computer except surf the web. I just don't get whats going on?? I can't install a a good majority of the included packages because I get errors like these. Its not even aMSN or VLC but a WHOLE number of applications that come up with this error. This is starting to make me worry because I installed ubuntu with the impression that I could use all these applications but right now this doesn't seem like the case! ](*,) 

Thanks in advance for anyone who is able to understand whats going on, cause I sure don't LOL :mrgreen: 

Peace!

---

### Post by taurus on 2006-12-29
Maybe you need to enable both universe and multiverse in /etc/apt/sources.list before you can install extra packages.  You can do that by removing the # in front of the lines with universe & multiverse at the end or near the end (with deb at the beginning)...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Save it and run

```
sudo aptitude update
sudo aptitude install vlc
```

---

### Post by todaymylove on 2006-12-29
**Right on!!** Your little method worked like a charm. Thanks a lot, taurus, i appreciate the quick response too! :)

---

### Post by taurus on 2006-12-29
> **todaymylove said:**
> **Right on!!** Your little method worked like a charm. Thanks a lot, taurus, i appreciate the quick response too! :)
You're welcome.  Now, you can "aptitude" whatever else you want.  ;)

---

