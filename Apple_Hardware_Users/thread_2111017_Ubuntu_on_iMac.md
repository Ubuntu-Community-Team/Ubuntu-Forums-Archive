---
title: "Ubuntu on iMac"
date: 2013-01-31
forum: Apple Hardware Users
---

### Post by mackgb on 2013-01-31
Hello,

Is here any one that have/had Ubuntu on iMac? I am looking for general support, advise and experience?

I am new and absolutely green when it comes to Ubuntu. Anything would be appreciated.

Administrators - If this post is on wrong forum let me know or amend it accordingly. 


Regards
Mack

---

### Post by mörgæs on 2013-01-31
As you suggested yourself, you were posing in the wrong forum. Moving to Apple.

If you begin a self-study here there's a good chance that you will find all you need.

---

### Post by iMac71 on 2013-02-01
> **mackgb said:**
> Hello,

Is here any one that have/had Ubuntu on iMac? I am looking for general support, advise and experience?

I am new and absolutely green when it comes to Ubuntu. Anything would be appreciated.

Administrators - If this post is on wrong forum let me know or amend it accordingly. 


Regards
Mackas my nickname says, i have an iMac mid 2007 (aka iMac 7,1 ;) ) on which I installed Ubuntu 12.04 64 bit.
My suggestion is to install the not Mac-specific 64 bit release, since at least as per my experience it works better than either the Mac-specific or the 32 bit.
Unity and Gnome Shell both run on Ubuntu: Unity is a desktop environment very similar to the traditional OS X desktop (even if it has the launcher on the left, while OS X has the dock at the bottom of the screen as default place), while Gnome Shell quite remembers Launchpad.
If you prefer a more Mac-like launcher, you may install [docky]("http://wiki.go-docky.com/index.php?title=Screenshots") and customize it in the same way of the OS X dock; another Mac-like dock is [cairo]("http://glx-dock.org/").

---

### Post by mackgb on 2013-02-01
Thanks for your reply. Which version would you suggest? I am currently on 12.10 64bit. 

Have you experience any issues or problems? My biggest one at the minute is the Bluetooth connectivity? How you overcame that or are  you using the wired keyboard? 

Sounds silly but how would I install other graphic environment?

---

### Post by iMac71 on 2013-02-01
> **mackgb said:**
> Which version would you suggest? I am currently on 12.10 64bit. As I wrote in my previous post, I suggest 12.04 64 bit not Mac-specific.> **mackgb said:**
> Have you experience any issues or problems? My biggest one at the minute is the Bluetooth connectivity? How you overcame that or are  you using the wired keyboard?Perhaps my iMac is too old for Ubuntu 12.10, but I've experienced problems with wireless internet connection: I lost the configuration after I've installed the updates.> **mackgb said:**
> Sounds silly but how would I install other graphic environment?**GNOME**:```
sudo apt-get install -y gnome-shell
```by this way you install three desktop environments:
gnome shell, the new desktop environment based on GNU Object Model Environment, aka GNOME;
gnome classic, a fallback of gnome3 similar to the classic gnome2 desktop;
gnome classic no effects, the same of the previous but without display effects;

**KDE**:```
sudo apt-get install -y kubuntu-desktop
```by this way you install the K desktop environment, aka KDE;

**XFCE**:```
sudo apt-get install -y xubuntu-desktop
```by this way you install the XForms Common Environment, aka XFCE;

**LXDE**:```
sudo apt-get install -y lubuntu-desktop
```by this way you install the Lightweight X11 Desktop Environment, aka LXDE.

---

### Post by mackgb on 2013-02-01
Thanks for your reply. I will try them as soon as I get chance, hopefully today.

Where did you learn all those terminal commands?

---

### Post by iMac71 on 2013-02-01
> **mackgb said:**
> Thanks for your reply. I will try them as soon as I get chance, hopefully today.if you wish to come back to "pure Ubuntu" after having tried those desktop environments, you may follow the instructions of this site:
[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)
> **mackgb said:**
> Where did you learn all those terminal commands?here:
[http://manpages.ubuntu.com/manpages/precise/en/](http://manpages.ubuntu.com/manpages/precise/en/)
AFAIK there aren't yet manual pages online for Ubuntu 12.10, aka quantal quetzal.

---

### Post by NobleYorkshire on 2013-02-02
> **iMac71 said:**
> if you wish to come back to "pure Ubuntu" after having tried those desktop environments, you may follow the instructions of this site:
[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)
here:
[http://manpages.ubuntu.com/manpages/precise/en/](http://manpages.ubuntu.com/manpages/precise/en/)
AFAIK there aren't yet manual pages online for Ubuntu 12.10, aka quantal quetzal.

Thanks for sharing these.  I use an iMac as well and am thinking about dual partitioning.  Right now I'm just running it as a Virtual Box which works well.  I have an older iMac as well so balancing the memory is a bit of an issue but overall works great.

---

### Post by iMac71 on 2013-02-02
> **NobleYorkshire said:**
> Thanks for sharing these.  I use an iMac as well and am thinking about dual partitioning.  Right now I'm just running it as a Virtual Box which works well.  I have an older iMac as well so balancing the memory is a bit of an issue but overall works great.the following link gives some informations about dual boot with OS X:
[https://help.ubuntu.com/community/DualBoot/MacOSX](https://help.ubuntu.com/community/DualBoot/MacOSX)
See also:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by iMac71 on 2013-02-02
here some websites you might wish to visit (click on the website name to go to the website itself):
[Easy Linux tips project]("https://sites.google.com/site/easylinuxtipsproject/")
[Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php")
both of the above guides are useful for finding help in many cases

[launchpad]("https://launchpad.net/") is very similar to Apple Developer's Connection, but in addition you may find on it useful informations about a lot of software

[Ask Ubuntu]("http://askubuntu.com/") is very similar to Apple discussions' site and, together with [Ubuntu Forums]("http://ubuntuforums.org/index.php") :D , gives a lot of tips and tricks for the best linux experience.

---

### Post by NobleYorkshire on 2013-02-02
> **iMac71 said:**
> here some websites you might wish to visit (click on the website name to go to the website itself):
[Easy Linux tips project]("https://sites.google.com/site/easylinuxtipsproject/")
[Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php")
both of the above guides are useful for finding help in many cases

[launchpad]("https://launchpad.net/") is very similar to Apple Developer's Connection, but in addition you may find on it useful informations about a lot of software

[Ask Ubuntu]("http://askubuntu.com/") is very similar to Apple discussions' site and, together with [Ubuntu Forums]("http://ubuntuforums.org/index.php") :D , gives a lot of tips and tricks for the best linux experience.

Thanks for sharing all these!  They are great resources!  Appreciated much!

---

### Post by mackgb on 2013-02-03
They are spot on. Thank you as well.

---

