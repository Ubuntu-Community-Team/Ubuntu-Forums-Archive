---
title: "apt-get packages not as up to date as they could be"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by gpaciga on 2006-11-15
Hopefully this is the right place to post this... I'm knew to linux on my personal computer (I've only used linux remotely before, but never had to set anything up myself). I'm using Kubuntu Dapper Drake. I've run into a problem where apt-get and adept don't seem to find the most up to date packages.

For example, when asking apt-get to install Firefox, it comes up with 1.5 but I know that there's a new 2.0 version. So, I downloaded and installed it myself. Now, I'm trying to install the mplayer plugin for Firefox, but I can't use apt-get to do it because apt-get doesn't know I have Firefox. It just wants to install Firefox 1.5 and give *that* version the plugin.

The real problem comes in when I download the mozilla-mplayer package myself and try to install it, I get all sorts of dependency errors saying my packages aren't up to date. Just like with Firefox, apt-get just doesn't see that there are more up to date packages out there to download.

So, I'd like to know the answer to any one of the following:
(1) How do I either upgrade these packages manually or convince apt-get to do it?
(2) How do I get an older version of mozilla-mplayer that doesn't have dependencies on new versions of these packages?
(3) How do I tell apt-get that I already have Firefox 2.0 installed so it can satisfy itself about that dependency and install the plugin?

I think addressing any one of these would fix the problem. But really, why wouldn't apt-get use the latest versions anyway? Are they not trustworthy enough?

The version of mozilla-mplayer I'm trying to install is the one at [http://packages.debian.org/unstable/misc/mozilla-mplayer](http://packages.debian.org/unstable/misc/mozilla-mplayer)

The exact dependency errors I'm getting are:

```
dpkg: dependency problems prevent configuration of mozilla-mplayer:
 mozilla-mplayer depends on libatk1.0-0 (>= 1.12.1); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 mozilla-mplayer depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 mozilla-mplayer depends on libcairo2 (>= 1.2.4); however:
  Version of libcairo2 on system is 1.0.4-0ubuntu1.
 mozilla-mplayer depends on libgcc1 (>= 1:4.1.0); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 mozilla-mplayer depends on libstdc++6 (>= 4.1.0); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.

```

but I think this is a general problem, not mozilla-plugin specific.

---

### Post by tuxcantfly on 2006-11-15
ubuntu dapper is not the latest version. upgrade to edgy if you want the latest, cutting-edge software [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by tuxcantfly on 2006-11-15
but, if you want to stay with dapper, you can always use equivs to create a dummy firefox package to satisfy the dependencies

---

### Post by gpaciga on 2006-11-15
Are you saying the updated packages are only available for Edgy? Then, how do I get the version of mozilla-mplayer that works on Dapper?

What is this "equivs" business? How do I make a dummy package?

---

### Post by karamba_kid on 2006-11-15
Firefox 2.0 hasn't been released officially for Dapper, and (I'm not a deveolper or anything) it may never be released for dapper.  If you want the cutting edge stuff you may want to look into installing edgy, but dapper will be supported for longer so I'm sticking with it. I don't have anyproblem with running older versions of applications you'll still get software updates as long as the developers are doing there job.  A handy comand to find out if apt is reporting the lastest stuff in the repositories is 
apt-cache policy foo
(where foo is the package name) then compare that with what you know is the latest package in the ubuntu repos.

---

### Post by jordanmthomas on 2006-11-15
Would you mind having 1.5 and 2.0 installed together?  If not, use the mplayer pluging from Ubuntu's repositories and install Firefox 1.5 as well.  Your Firefox 2 will see the plugin no problem.

(This is exactly what I have done on my FC6 box, but it does suck having Firefox installed twice for no reason)

Also, you might want to check into diverting packages.  I've never done it, so I won't tell you how, but search around for how to divert files from certain packages.  You could install Firefox 1.5, but divert it to /dev/null so apt thinks it's installed, but it won't take up any space.

---

### Post by tuxcantfly on 2006-11-15
to create a dummy pacakge with equivs:

sudo apt-get install equivs
equivs-control firefox
gedit ./firefox

then, substitue the values and versions in the file and save

equivs-build firefox
sudo dpkg -i ./firefox.deb

---

