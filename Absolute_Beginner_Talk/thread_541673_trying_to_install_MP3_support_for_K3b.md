---
title: "trying to install MP3 support for K3b"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by macruadhi on 2007-09-03
When trying to install MP3 decoder for K3b I get this error screen:


[IMG]<img src="http://i143.photobucket.com/albums/r125/macruadhi/Screenshot-1.png >[/IMG]

Here's what the dialog box says:
libk3b2-mp3:
  Depends: kdelibs4c2a (>=4:3.5.3-1) but 4:3.5.2-0ubuntu18.5 is to be installed
  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20.5 is to be installed
 Depends: libdbus-1-3  but it is not installable
  Depends: libdbus-qt-1-1c2 (>=0.62.git.20060814) but 0.60-6ubuntu8.1 is to be installed
  Depends: libfreetype6 (>=2.2) but 2.1.10-1ubuntu2.4 is to be installed
  Depends: libgcc1 (>=1:4.1.1-11ubuntu1) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libstdc++6 (>=4.1.1-11ubuntu1) but 4.0.3-1ubuntu5 is to be installed


I'm  not sure where else to go with this.

---

### Post by mckryptyk on 2007-09-03
Here you go:

```
sudo apt-get install libk3b2-mp3
``` 

Cheers.

---

### Post by macruadhi on 2007-09-03
And here's what I get:

eric@eric-laptop:~$ sudo apt-get install libk3b2-mp3
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libk3b2-mp3: Depends: kdelibs4c2a (>= 4:3.5.3-1) but 4:3.5.2-0ubuntu18.5 is to be installed
               Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.5 is to be installed
               Depends: libdbus-1-3 but it is not installable
               Depends: libdbus-qt-1-1c2 (>= 0.62.git.20060814) but 0.60-6ubuntu8.1 is to be installed
               Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.4 is to be installed
               Depends: libgcc1 (>= 1:4.1.1-11ubuntu1) but 1:4.0.3-1ubuntu5 is to be installed
               Depends: libstdc++6 (>= 4.1.1-11ubuntu1) but 4.0.3-1ubuntu5 is to be installed
E: Broken packages

---

### Post by mckryptyk on 2007-09-03
Please enter this command and copy it's output from terminal to the forum.

```
cat /etc/apt/sources.list
```

Also please post this one as well.

```
sudo uname -a 
```

Thank You.

---

### Post by macruadhi on 2007-09-03
Repo list:

     deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main
    deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main
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
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univer se multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted un iverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe mu ltiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main


#AUTOMATIX REPOS END
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free


AND

eric@eric-laptop:~$ sudo uname -a
Password:
Linux eric-laptop 2.6.15-28-386 #1 PREEMPT Wed Jul 18 22:50:32 UTC 2007 i686 GNU/Linux



Thanks all!!!!

---

### Post by annda on 2007-09-03
hmm, i'm not an expert but using both dapper and edgy repositories can get you into this sort of trouble. try disabling the edgy repository to avoid the versions mixup.

---

### Post by stmiller on 2007-09-04
> **macruadhi said:**
> 
#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main




I'm afraid Automatix has caused a conflict with your system. Do not use Automatix, as it will [trash your system]("http://mjg59.livejournal.com/77440.html"). It is not supported by Ubuntu, nor is it compatible with Ubuntu's packages.

The best thing to do is delete that automatix line, and the 'blognux' lines  (and change that edgy word in there to dapper) then run

```

sudo apt-get update

sudo apt-get autoclean

sudo apt-get autoremove

sudo apt-get upgrade

```

---

### Post by mckryptyk on 2007-09-04
I'm going to have to agree, using automatix *can* and *will * destroy system integrity.

This still doesn't seem to answer why you can't install libk3b2-mp3, but certainly could be the culprit.

Perhaps, you could try installing libk3b2-mp3 from the repos, by searching for k3b and right-clicking on it, then selecting "mark suggested for installation". In that menu, you will find libk3b2-mp3. Post back how this works for you.

I am wondering if you have thought of upgrading to feisty as it is fairly stable, now that canonical is working to finish up on gutsy gibbon.

The advantage to doing so would be to wrestle back control from automatix, by upgrading from selected repositories (ubuntu, medibuntu) and away from automatix and it's choice of repos. This could bring you back in line with the direction ubuntu is headed with the distribution.

The downside is that without careful planning first, there may be odd quirks to work out later.

If you are interested in this, you should begin research into how to do this.

message me if you are stuck,

Cheers.

---

