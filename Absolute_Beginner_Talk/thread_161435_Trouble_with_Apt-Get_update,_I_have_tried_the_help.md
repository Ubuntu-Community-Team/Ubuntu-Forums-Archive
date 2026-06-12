---
title: "Trouble with Apt-Get update, I have tried the help yourself recommendations, SOS"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by lg3 on 2006-04-17
I run apt-get update and the output I get is below:


leroy@user2:~$ sudo apt-get update
Get:1 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Get:2 [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release.gpg [65B]
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release [702B]
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release.gpg
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Hit [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Ign [http://theli.free.fr](http://theli.free.fr) ./ Packages
Hit [http://theli.free.fr](http://theli.free.fr) ./ Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  403 Forbidden [IP: 82.211.81.151 80]
99% [Connecting to ftp.free.fr (213.228.0.141)]


-----
Eventually it times out and tells me it didn't work. Anybody help on this one?
I appreciate it immensely.
LeRoy

---

### Post by dermotti on 2006-04-17
Maybe you shoudl try a more generic sources.ls, yours sources look funky.

---

### Post by lg3 on 2006-04-17
Thanks for the post. I am not sure what you mean by more generic sources, could you post an example of a more generic source? I appreciate the help.

---

### Post by lg3 on 2006-04-17
Also, more specifically the problem seems to be the 403 Forbidden situation than anything else. How do I fix the 403 Forbidden situation? Thank you for the noob support.

---

### Post by WoodyMahan on 2006-04-17
Hey lg

Check out the instructions I provided on one of your other threads:
[http://www.ubuntuforums.org/showthread.php?t=161521](http://www.ubuntuforums.org/showthread.php?t=161521)

Follow these instructions and it is likely you will fix this issue as well.

---

### Post by lg3 on 2006-04-17
Thanks for the direction. I will check it out and let you know if it works. Appreciate it.////////
Worked!!! Thanks for the help.

---

