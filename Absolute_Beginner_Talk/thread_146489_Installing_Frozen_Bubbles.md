---
title: "Installing Frozen Bubbles"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by bpazolli on 2006-03-18
Hi, I have just finished installing the PPC edition of Ubuntu 5.10 on my iMac 333. Everything has gone great. I now want to install my first application. I have formed a liking to Frozen Bubbles. Can anyone tell me if it is possible to install it and if so how? Any help would be appreciated.

Thank You,
Ben Pazolli

---

### Post by Zelut on 2006-03-18
quick way (from the command line) would be to try the following:

sudo apt-get install frozen-bubbles

You can also try searching for it thru Synaptic (System > Admin > Synaptic) and install it that way.  Let me know how that works..

---

### Post by bpazolli on 2006-03-18
I tried typing what you said into the terminal and I got this:

[I]Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package frozen-bubbles[/I]

I may be new to linux but I think it couldn't find the pakage.

Thanks for the help,
Ben Pazolli

---

### Post by FizDev on 2006-03-18
You need to add a certain repository in your sources.list... I think it's the universe but not sure. Anyway,to do this :
```
sudo gedit /etc/apt/sources.list
```
then remove the ## of the line where there is 
> ## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
save and exit.
After that, do:
```
sudo apt-get update
```
```
sudo apt-get install frozen-bubble
```

---

### Post by Madpilot on 2006-03-18
A couple of pages that might help:
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
[http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto)

And, for an 'official' sources.list with all the standard repos enabled, have a look at this:
[http://paste.ubuntu-nl.org/6047](http://paste.ubuntu-nl.org/6047)

---

### Post by bpazolli on 2006-03-18
Did everything you said got the same result:

[I]xxx@xxx:~$ sudo apt-get update
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release [30.9kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Sources
Get:5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/universe Sources [915kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [43.5kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [1625B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [13.4kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:11 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages [35.7kB]
Get:12 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:13 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Sources [17.5kB]
Get:14 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Fetched 1086kB in 25s (43.3kB/s)
Reading package lists... Done
xxx@xxx:~$ sudo apt-get install frozen-bubble
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package frozen-bubble
[/I]

---

### Post by Sef on 2006-03-18
Applications > Add Applications > Games > More programs >click on  frozen bubble > click apply > click again > installed after few minutes.

---

### Post by bpazolli on 2006-03-18
Good News. I got Frozen Bubble installed by using Synaptic, after changing the respository. Must of not edited the sources.list file right.

Now I have a new problem the program works but I get no sound. I read somewhere that downloading libsdl1.2debian-all fixes it. So now instead of no sound I get a horrible static noise, unless I turn off the sound. Sound works in other parts of the system.

Thanks for the help,
Ben Pazolli

---

### Post by Sef on 2006-03-18
> downloading libsdl1.2debian

If that is the fix, go back into synaptic, and search for it.  Then download it.

---

### Post by FizDev on 2006-03-18
Depending if you use OSS, ESD, or Alsa, you could also do :
```
sudo apt-get install libsdl1.2debian-esd
```

---

### Post by bpazolli on 2006-03-19
Thanks for the help. I was telling a someone else about how it wasn't working and he started it up and for some reason it worked. What I meant was that I installed libsdl1.2debian-all when there was no sound and after the installation there was static instead of sound. Then I uninstalled it and went back to what I had before and it seemed to go back to no sound. Now for some reason it works.

Thanks very much,
Ben Pazolli

---

### Post by Sef on 2006-03-19
yw.  Sometimes things just work when u least expect it.

---

