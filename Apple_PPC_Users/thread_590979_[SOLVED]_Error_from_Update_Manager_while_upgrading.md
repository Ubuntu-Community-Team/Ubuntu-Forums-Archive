---
title: "[SOLVED] Error from Update Manager while upgrading to 7.04"
date: 2007-10-25
forum: Apple PPC Users
---

### Post by magnolia fan on 2007-10-25
I'm receiving the following errors  from Update Manager while upgrading to 7.04.  The errors stop the installation before it gets started:

"Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-powerpc/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-powerpc/Packages.bz2) Sub-process bzip2 returned an error code (2)

Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-powerpc/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-powerpc/Packages.bz2) Sub-process bzip2 returned an error code (2)"


-----

Here is my sources.list file:

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by Tommy on 2007-10-25
So the upgrade has stopped BEFORE it has updated your sources.list to Feisty.

I don't know where the upgrade manager pulls the files it uses -- assuming they're not IN the security repository, you can try commenting out the four security lines for the purposes of this upgrade. (Two of the deb lines pointing to edgy-security in your source are actually redundant, and you can combine them into one line if you want. The deb-src edgy-security line is irrelevant to the upgrade.)

Someone else may know better, but I believe there was a bug in Edgy that was putting erroneous source lines in the PowerPC sources.list -- so you may be suffering from that bug. It probably means you have NEVER had a security update.

I don't know the consequences of doing an upgrade if the security repo doesn't work, but ultimately all those repositories get switched anyway so I'm guessing you'll probably be OK.

---

### Post by magnolia fan on 2007-10-26
SUCCESS!

I commented out all Security sources except "deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted" from the sources.list and re-ran the updgrade.  No problems to report.

-thanks for the help.

---

### Post by Tommy on 2007-10-29
> **magnolia fan said:**
> I commented out all Security sources except "deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted" from the sources.list and re-ran the updgrade.  No problems to report.


I'm glad it worked! Be sure to check your /etc/apt/sources.list to make sure the upgrade tool left the security sources active -- it PROBABLY did, but of course there was something wrong in the first place so it wouldn't hurt to check.

You may also have seen some security updates come through by now, so if you have it probably means it's working.

---

