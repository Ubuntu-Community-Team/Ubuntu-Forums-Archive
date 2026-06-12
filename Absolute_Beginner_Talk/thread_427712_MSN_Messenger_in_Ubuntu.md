---
title: "MSN Messenger in Ubuntu"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by hackman on 2007-04-29
As some of you may know i have been having problems with aMSN so i was wondering if it works to use the real MSN Messenger using Wine in Ubuntu

p.s sorry if that doesn't make since

---

### Post by zetsumei on 2007-04-29
just use GAIM it allows for MSN, AIM, ICQ, and a lot more...It's installed by default.

---

### Post by starcraft.man on 2007-04-29
If you really want the feel of windows live, I recommend installing the newest 0.97 aMSN.

There are five debian packages, its easy to figure the order based on which need which. All of them are listed on this link, 4 at the top, 1 is further down just look for the deb in the link. [Link!]("http://ubuntuforums.org/showthread.php?t=416062&highlight=new+amsn")

Have fun!

---

### Post by hackman on 2007-04-29
> **zetsumei said:**
> just use GAIM it allows for MSN, AIM, ICQ, and a lot more...It's installed by default.

I don't really like gaim but i'm using it now

---

### Post by zetsumei on 2007-04-29
I hardly use IM any more but I still have GAIM just because I'm to lazy to install anything else LOL

---

### Post by Hackza on 2007-04-29
I'm using aMSN 0.97b and it really is like live. If I were you, I'd go with trying out what starcraft.man posted. You get all the functions like winks and handwriting with the plugins aswell

---

### Post by hackman on 2007-04-29
> **starcraft.man said:**
> If you really want the feel of windows live, I recommend installing the newest 0.97 aMSN.

There are five debian packages, its easy to figure the order based on which need which. All of them are listed on this link, 4 at the top, 1 is further down just look for the deb in the link. [Link!]("http://ubuntuforums.org/showthread.php?t=416062&highlight=new+amsn")

Have fun!

thanks i'll try it!

---

### Post by hackman on 2007-04-29
still dosn't work this is what it does when i try to switch user: 
[IMG]http://img2.freeimagehosting.net/uploads/3ee4e46643.png[/IMG]

---

### Post by Pobega on 2007-04-29
ps aux | grep msn

kill -9 any of the processes that are running with the name amsn, using the process' PID.

Restart aMSN.

---

### Post by cumanzor on 2007-04-29
Does aMsn have personal messages (below the nickname)? This, and msgplus are the only things keeping me from using any other IM than WLM.

---

### Post by medya on 2007-04-29
i think you should delete the Cache fodler of your aMSN , it should a hidden folder ,

first uninstall your aMSN thourgh synaptic package manager then go to your home directory , and then CTR+H
and then search for aMSN folder , and go there and delete everything !
and now re-install your aMSN through synaptic package manager..

I hope it helps !

---

### Post by Hackza on 2007-04-29
it indeed does have personal messages. have a look at the plugins on their site but also some are 0.97b only and in the forum like winks so your probably best googling "amsn personal message" and see if it does it. that will probably reap good results. I've found the 0.97 aMSN good and I've been on msn with msgplus for years and only *thinks* last week started linux.

---

### Post by hackman on 2007-04-29
> **medya said:**
> i think you should delete the Cache fodler of your aMSN , it should a hidden folder ,

first uninstall your aMSN thourgh synaptic package manager then go to your home directory , and then CTR+H
and then search for aMSN folder , and go there and delete everything !
and now re-install your aMSN through synaptic package manager..

I hope it helps !

That sounds like it'll work i'll try it now.
And report back

---

### Post by hackman on 2007-04-29
ok i uninstalled it and deleted the .aMSN folder 
but now when i try to install it thru Synaptic Package Manager it says:

[[img]http://img2.freeimagehosting.net/uploads/d8c8c334f8.png[/img]](http://www.freeimagehosting.net/)

---

### Post by starcraft.man on 2007-04-29
Ummm, just a question but was there something wrong with my debian files? They can be used as many times as you reinstall... not to mention the repos have older versions than the debs. (Haven't seen any noticeable instability with 0.97 either).

If your set on the old version, I'd recommend just using the command line.

```
sudo aptitude install amsn
```

Should install the old version for ya.

---

### Post by hackman on 2007-04-29
> **starcraft.man said:**
> 

```
sudo aptitude install amsn
```

Should install the old version for ya.

ok this is what the termial says:

psphackman@psphackman-laptop:~$ sudo aptitude install amsn
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
psphackman@psphackman-laptop:~$

---

### Post by starcraft.man on 2007-04-29
> **hackman said:**
> ok this is what the termial says:

psphackman@psphackman-laptop:~$ sudo aptitude install amsn
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
psphackman@psphackman-laptop:~$

Means another manager is accessing your system for installs and wants exclusive access to your drive. Close the package manager and any other installer you have open. Then retry, if it persists... log out and back in, a simple fix to terminate any open install.

---

### Post by hackman on 2007-04-29
> **starcraft.man said:**
> Means another manager is accessing your system for installs and wants exclusive access to your drive. Close the package manager and any other installer you have open. Then retry, if it persists... log out and back in, a simple fix to terminate any open install.

wow your smart it kinda worked but i'm a noob so what do i do with this?

```
psphackman@psphackman-laptop:~$ sudo aptitude install amsn
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  amsn 
The following NEW packages will be automatically installed:
  docker 
The following NEW packages will be installed:
  docker 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2559kB of archives. After unpacking 9413kB will be used.
The following packages have unmet dependencies:
  amsn: Depends: tcl8.4 which is a virtual package.
        Depends: tk8.4 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
amsn [Not Installed]

Score is -10001

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?

```

---

### Post by starcraft.man on 2007-04-29
> **hackman said:**
> wow your smart it kinda worked but i'm a noob so what do i do with this?

```
psphackman@psphackman-laptop:~$ sudo aptitude install amsn
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  amsn 
The following NEW packages will be automatically installed:
  docker 
The following NEW packages will be installed:
  docker 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2559kB of archives. After unpacking 9413kB will be used.
The following packages have unmet dependencies:
  amsn: Depends: tcl8.4 which is a virtual package.
        Depends: tk8.4 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
amsn [Not Installed]

Score is -10001

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?

```

Uh, geez... hmmm, I have no idea what the score of -10001. I am also not sure what broken means except that when you uninstalled aMSN it didn't remove completely and something was left.

Run :
 ```
sudo aptitude remove amsn
```

(A note, Aptitude removes all dependencies... apt-get leaves dependencies in your computer. We want aptitude to give you a clean slate.)

After thats done, I'd try the 5 debian packages. There shouldn't be any reason those don't work, since the 4 before the amsn 0.97 deb install all the dependencies you need.

PS: I'm not that smart, just been using Ubuntu for 1 and a half months :P.

---

### Post by hackman on 2007-04-29
well this is to much of a hassle so i'm just going to install xp and to hell with ubuntu and linux (but beryl is cool)

good bye ubuntu forums and thanks for your help :) 

psphackman, goodday

---

### Post by starcraft.man on 2007-04-29
> **hackman said:**
> well this is to much of a hassle so i'm just going to install xp and to hell with ubuntu and linux (but beryl is cool)

good bye ubuntu forums and thanks for your help :) 

psphackman, goodday

come on... you can't quit ubuntu just over an IM client..... I mean, give it a bit more time than that.

---

### Post by jiminycricket on 2007-04-29
OP: have you tried Kopete?

---

### Post by Atmosphere on 2007-04-29
Kopete is only for KDE isn't it ? so you would have to use Kubuntu or another KDE distro

edit : nevermind just learnt that software is interchangable between environments

gotta love linux... learn something new everyday.

---

### Post by flapane on 2007-05-16
any way to see coloured nicks in amsn like in msn live?

---

