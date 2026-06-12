---
title: "sudo apt-get update HELP"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by tbuss on 2007-03-25
When I run **sudo apt-get update** everything runs fine until the very end. I get this:

```
Fetched 5569B in 4s (1137B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/Release  Unable to find expected entry  multiversedeb/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I pasted the url in the web browser and was able to connect. 
I tried uncommenting the entry in sources.list and adding **deb** This is the result:
```

tbuss@tbuss-desktop:/home$ sudo apt-get update
E: Malformed line 16 in source list /etc/apt/sources.list (dist)
```

I then deleted the **deb** entry and added **multiversedeb** This is the result:
```
tbuss@tbuss-desktop:/home$ sudo apt-get update
E: Type 'multiversedeb' is not known on line 16 in source list /etc/apt/sources.list
```

Finally I deleted the **mutliverse** and added **deb-src **Same result:
```

tbuss@tbuss-desktop:/home$ sudo apt-get update
E: Malformed line 16 in source list /etc/apt/sources.list (dist)
```

This is my sources.list as is. What else can I try to get this error to go away? Update says it Fails to Fetch, but the source is commented out. If I try to uncomment the source I receive errors?
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/ ./
deb-src http://giss.tv/~vale/ubuntu32 ./
deb-src http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/ ./
deb http://www.debian-multimedia.org/ sid main
deb http://www.kiberpipa.org/~muzzol/cinelerra/edgy-i386/ ./
deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiversedeb http://giss.tv/~vale/ubuntu32 ./
deb http://flomertens.keo.in/ubuntu/ edgy main main-all
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian ./
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./

**##http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/Release **

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen

#ubuntu edgy
deb http://giss.tv/~vale/ubuntu32 ./
deb-src http://giss.tv/~vale/ubuntu32 ./

# Repository for wine
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main
```

---

### Post by useResa on 2007-03-25
Was the original line in your sources.list, just
> **[http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/Release](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/Release)**

If you would like to use this repository, the lines should be
>  deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
This  does not give any errors when used in my sources.list.

Hope this will solve it for you too.

---

### Post by tbuss on 2007-03-25
useResa

I tried the repositiry you listed, same results:

Fetched 5569B in 5s (1043B/s)
F**ailed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/Release](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/Release)  Unable to find expected entry  multiversedeb/binary-i386/Packages in Meta-index file (malformed Release file?**)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
tbuss@tbuss-desktop:/home$

---

### Post by useResa on 2007-03-25
Just read your reply and tried your sources.list just for confirmation (sorry).
Had the same problem. However, searching I found [this bug](https://launchpad.net/launchpad-publisher/+bug/54037) listed, which exactly describes your problem.

AFAIK it has not been resolved yet.
Maybe someone else can help you further.
It stops here for me, sorry :(

---

### Post by tbuss on 2007-03-27
userResa,

Thanks for the reply, I'm unsure of what to do with the information listed on the site you linked to.

What is cron.daily 

The site suggested that the bug was fixed but I'm still having the same problem.

---

### Post by tbuss on 2007-03-27
userResa,

nevermind the previous post. 

Is there a way to just remove the the entry somehow? I removed the repository but everythime I run an update or upgrade it prompts that it failed to fetch from it. Is it possiblle it could be located somewhere else besides the sources.list?

---

### Post by useResa on 2007-03-27
Sorry, that I did not notice this first, but I just now discovered you had a typo and duplicate entries in your sources.list

As a fourth entry you have indicated
>  deb-src [http://giss.tv/~vale/ubuntu32]("http://giss.tv/%7Evale/ubuntu32") ./But you also have that at the end of your file (just before the WINE repositories)
Next I noticed that you have the entry
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiversedeb [http://giss.tv/~vale/ubuntu32]("http://giss.tv/%7Evale/ubuntu32") ./
For some reason the enter between multiverse and the next deb statement was missing.
But then again ... the line follwing multiverse deb [http://giss.tv/~vale/ubuntu32]("http://giss.tv/%7Evale/ubuntu32") ./ is also a double entry. 

I have tried an apt-get update with the following sources.list and that works.
Hope that my explanation is somehow clear and that it helps.
> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb [http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/](http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/) ./
# deb-src [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
deb-src [http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/](http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/) ./
deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) sid main
deb [http://www.kiberpipa.org/~muzzol/cinelerra/edgy-i386/](http://www.kiberpipa.org/~muzzol/cinelerra/edgy-i386/) ./
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse
# deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian) ./
deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

##[http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/Release](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/Release) 

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

#ubuntu edgy
# deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
# deb-src [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./

# Repository for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

Good luck and hope it is solved now.
Once again sorry for not noticing this earlier.

---

### Post by tbuss on 2007-03-27
yep, that did it, 

Just in time too, I was going insane trying to figure this out, no big deal, just wanted the error to go away.

Thanks for the edited sources.list, I just don't know what to look for yet, Thanks.

---

### Post by useResa on 2007-03-27
> **tbuss said:**
> yep, that did it, 

Just in time too, I was going insane trying to figure this out, no big deal, just wanted the error to go away.

Thanks for the edited sources.list, I just don't know what to look for yet, Thanks.
Glad that I could be of help.
Enjoy the ride.

---

