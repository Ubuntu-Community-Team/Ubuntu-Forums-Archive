---
title: "Some repositories not working?"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Bartender on 2006-10-31
Over at a friend's house, his PC won't get some updates

[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:) 404 Not Found

I'm kinda guessing on what to do.  Went to Synaptic, enabled every single repo in the list, still get this message when trying to update.  What am I missing?

Well, that didn't help any.  The links were shortened.  I'll try again.  Synaptic is now saying there are no updates, so maybe there are obsolete repoitories in his sources list?

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

 Is there a bad repo in here?

---

### Post by John.Michael.Kane on 2006-10-31
Try editing your sources.list.removing the **us** country code,and replace with **se** country code.
run sudo aptitude update.

---

### Post by Bartender on 2006-11-01
Changing to 'se' made Synaptic completely unresponsive.  At least with 'us' it started to get packages.  On his DSL modem progress would slow to a crawl, then we'd get 'disconnected' or 'could not find' messages.
Figured there was too much traffic and called it a day.  At 0500 PST (West Coast USA) I tried reloading the Synaptic lists at home on our pathetic dial-up line.  When Synaptic got to the us servers the traffic slowed to 1 kbps or less, but it finally finished.  Sheesh  

I'm guessing that maybe my friend's DSL modem gives up when traffic falls below a certain speed?  Our US Robotics dial-up modem continued soldiering on at 1 kbps.

At first I thought that the Edgy traffic was slowing things down, but why would the dapper servers be affected by edgy traffic?

I haven't seen anyone else comment on impossibly slow downloads.  Seems like there'd be some talk about this.

---

