---
title: "403 forbidden"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by naga123 on 2005-10-07
when I tried to update ubuntu using **apt-get update** I get 403 forbidden. 

when I googled for it I found this
[B]403 Forbidden
    The server understood the request, but is refusing to fulfill it. Authorization will not help and the request SHOULD NOT be repeated. If the request method was not HEAD and the server wishes to make public why the request has not been fulfilled, it SHOULD describe the reason for the refusal in the entity. This status code is commonly used when the server does not wish to reveal exactly why the request has been refused, or when no other response is applicable.[/B]

Does this mean that **Ubuntu server is refusing** or **my parent proxy (my pc is connect to internet through proxy)is refusing it**.
plz help me...........

---

### Post by Mustard on 2005-10-07
Is this the first time you have run update?  Has it worked before?

---

### Post by nitricacid on 2005-10-07
Is the '403 Forbidden' the only message you get?
What version of ubuntu are you using?

It sounds to me like some, if not all of the links in the sources.list are bad.
I remember seeing something about a Maxwell.org/something or other link that is no longer supported by ubuntu.

---

### Post by Kapre on 2005-10-07
Before I would say that your parent proxy is refusing your connection, could you please advise if you already uncommented (meaning you've already removed all  the "#") in the sources.list.

If those are already removed, then you might want to check with your proxy settings.

K

---

### Post by naga123 on 2005-10-08
when I run it 2 weeks back it is ok.  I'm facing this problem recently.

 my proxy setting are correct.


Iam icluding my sources.list........


 
> #deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multivers


---

### Post by Mustard on 2005-10-08
Your source.list looks fine.  I wonder whether its an issue with your ISP.

---

### Post by Hobbsee on 2005-10-08
> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multivers

at the end of your sources list, multiverse should probably be spelt with an "e" on the end :P

---

### Post by Mustard on 2005-10-08
[QUOTE=Hobbsee]at the end of your sources list, multiverse should probably be spelt with an "e" on the end :P[/QUOTE]

Well spotted. :)

Copy and paste error or answer to the problem?  *drum roll*

/me waits expectantly for the answer......

---

### Post by naga123 on 2005-10-09
> 403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  403 Forbidden
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
  403 Forbidden
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  403 Forbidden
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  403 Forbidden
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  403 Forbidden
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  403 Forbidden
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  403 Forbidden
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  403 Forbidden
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
  403 Forbidden
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
  403 Forbidden
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
  403 Forbidden
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
  403 Forbidden
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
  403 Forbidden
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
  403 Forbidden
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
  403 Forbidden
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
  403 Forbidden
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
  403 Forbidden
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
  403 Forbidden
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
  403 Forbidden
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
  403 Forbidden
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
  403 Forbidden
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
  403 Forbidden
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
  403 Forbidden
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
  403 Forbidden
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
  403 Forbidden
Reading package lists...



this is the error

---

### Post by FLeiXiuS on 2005-10-09
sudo iptables --list

---

### Post by naga123 on 2005-10-10
sudo iptables --list

the output:

> Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


---

### Post by FLeiXiuS on 2005-10-10
Are you located behind any other firewalls?  Perhaps this is a work machine which is preventing access to this location.  

Can you browse the web?

---

### Post by FLeiXiuS on 2005-10-10
Are you located behind any other firewalls?  Perhaps this is a work machine which is preventing access to this location.  

Can you browse the web?

Does this link work for you?
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/](http://us.archive.ubuntu.com/ubuntu/dists/breezy/)

---

### Post by naga123 on 2005-10-12
I can access web.
Iam able to access [http://us.archive.ubuntu.com/ubuntu/dists/breezy/](http://us.archive.ubuntu.com/ubuntu/dists/breezy/)

but I get 403 forbidden error when using **apt-get update**

---

