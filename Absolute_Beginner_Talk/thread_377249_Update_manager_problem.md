---
title: "Update manager problem"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by HdK on 2007-03-05
When I try to use update manager , it quickly opens and then closes. I go to the K at the bottom left of the screen then I pick System and then Update Manager. I have no idea why it is not working correctly

---

### Post by taurus on 2007-03-05
Can you post the outputs of these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by HdK on 2007-03-05
i get this error

hdk@hdk-desktop:~$ sudo aptitude update
E: Malformed line 44 in source list /etc/apt/sources.list (dist)
E: Malformed line 44 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.

---

### Post by taurus on 2007-03-05
There is something wrong with line 44 in /etc/apt/sources.list.  So, you can either fix it or post your /etc/apt/sources.list here then.

```
cat /etc/apt/sources.list
```

---

### Post by HdK on 2007-03-05
i get this 

hdk@hdk-desktop:~$ cat /etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
#AUTOMATIX BLEEDER REPOS START
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX BLEEDER REPOS END
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-frdeb
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz)
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/)
hdk@hdk-desktop:~$

---

### Post by taurus on 2007-03-05
The last two lines look a little off so edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the last two lines.  Save it and run those two commands again.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by HdK on 2007-03-05
Thank you soo much taurus:)

---

### Post by taurus on 2007-03-05
You're welcome.

---

