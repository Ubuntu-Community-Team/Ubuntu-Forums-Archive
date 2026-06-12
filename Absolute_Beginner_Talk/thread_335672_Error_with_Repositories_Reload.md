---
title: "Error with Repositories Reload"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2007-01-10
When I reload my repositories in -->Synaptic Package Manager -->Settings -->Repositories I get the following error message:> The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[COLOR="Red"][http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz:) Sub-process gzip returned an error code (1)[/COLOR] I never know if my updates are complete or faulty. What is wrong? Here is my sources.list
> ### Original /etc/apt/sources.list ###  
### added Automatix Repos. November 2006 ###
### added KDE.org Repositories. November 2006 ###
### added Beryl-Project.org Repos. December 2006
#
### Ubuntu MAIN ###
#
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
#
### Ubuntu BUG FIX UPDATES ###
#
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
#
### Ubuntu UNIVERSE ###
#
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
#
### Ububtu BACKPORTS ###
#
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
#
### Ubuntu SECURITY UPDATES ###
#
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
#
### Kubuntu.org repositories. Packages for the latest KDE version ###
#
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main
deb [http://kubuntu.org/packages/kde-355](http://kubuntu.org/packages/kde-355) edgy main
# deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main
#
### Ubuntu BERYL- PROJECT ###
#
# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
#
### AUTOMATIX REPOS START ###
#
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#
### AUTOMATIX REPOS END ###


---

### Post by Cariboo1938 on 2007-01-12
Bummmm....](*,) 
Any reply or opinion on that issue is highly appreciated...!
Thanks

---

### Post by Modernity on 2007-01-12
Try this. This is what you have.

```

### Kubuntu.org repositories. Packages for the latest KDE version ###
#
deb http://kubuntu.org/packages/kde-latest edgy main
deb http://kubuntu.org/packages/kde-355 edgy main
# deb-src http://kubuntu.org/packages/kde-latest edgy main
#


```

Change to this:

```

### Kubuntu.org repositories. Packages for the latest KDE version ###
#
deb http://kubuntu.org/packages/kde-latest edgy main
deb http://kubuntu.org/packages/kde-355 edgy main
deb-src http://kubuntu.org/packages/kde-latest edgy main
#


```

---

### Post by Cariboo1938 on 2007-01-13
> **Modernity said:**
> 
Change to this:
```

### Kubuntu.org repositories. Packages for the latest KDE version ###
#
deb http://kubuntu.org/packages/kde-latest edgy main
deb http://kubuntu.org/packages/kde-355 edgy main
deb-src http://kubuntu.org/packages/kde-latest edgy main
#

```
Thanks for the response! I uncommented the line 'deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main' but it didn't help.
I don't understand why I get this message> [url]http://archive.ubuntu.com/ubuntu/dists/
edgy-updates/main/binary-amd64/Packages.gz:[/url] Sub-process gzip returned an error code (1)when "archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz" is not even in my sources.list.:confused:

---

### Post by mikewhatever on 2007-02-03
I wonder if the problem has been solved, and if so, how?

---

### Post by Cariboo1938 on 2007-03-10
> **mikewhatever said:**
> I wonder if the problem has been solved, and if so, how?
Hello Mike,
No, the error message, as described earlier, still comes up after 'Reload'. I attached the Screen Shots.
:confused:

---

