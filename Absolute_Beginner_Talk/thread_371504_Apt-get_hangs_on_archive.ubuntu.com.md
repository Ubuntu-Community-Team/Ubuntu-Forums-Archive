---
title: "Apt-get hangs on archive.ubuntu.com"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by dolphinsonar on 2007-02-27
I uninstalled synaptic, and am trying to reinstall.  I type into the terminal

[PHP]sudo apt-get install synaptic[/PHP] and it goes through the normal list of commands.  Then it gets stuck on

[PHP]Connecting to archive.ubuntu.com (91.189.89.6)[/PHP] and hangs.

Any suggestions?  I figure that I could probably tell apt-get to look somewhere else for the package "synaptic" like a mirror, but I can't quite figure out how to do this.

---

### Post by Kateikyoushi on 2007-02-27
Did you do an update before you tried this ?

[CODEE]sudo aptitude update
sudo aptitude install synaptic[/CODE]

If doesn't work what's your sources.list ?

```
cat /etc/apt/sources.list
```

---

### Post by dolphinsonar on 2007-02-27
Tried

```
sudo apt-get install update
```No luck, still hangs at the same spot.  Here is my sources.list

## Main and Restricted components
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major Bugfixes
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe #Added by software-properties

## Security Fixes to main and restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties

## Security fixes to universe/multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

## BUMPS metapackage repo and seveas' repo
deb [http://www.politicalcrossfire.com/ubuntu/bumps](http://www.politicalcrossfire.com/ubuntu/bumps) dapper main
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all

## Universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy multiverse

---

### Post by Kateikyoushi on 2007-02-27
Try to change the url in the line which gives the error from http to ftp:// .

---

### Post by dolphinsonar on 2007-02-27
Same difference when I change http:// to ftp://

---

### Post by Kateikyoushi on 2007-02-27
Interesting because the IP is correct and neither protocol works, therefore I assume changing the servers wouldn't help either.

---

### Post by dolphinsonar on 2007-02-27
It gets stuck on archive.ubuntu.com but that isn't even listed in my sources.list after I just changed it to this:

```
deb http://dk.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ edgy main restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ edgy-updates main restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://dk.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted #Added by software-properties
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt edgy main

deb http://dl.google.com/linux/deb/ stable non-free

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
#AUTOMATIX REPOS END

# Treviño's Ubuntu edgy Beryl-SVN Repository (GPG key: 81836EBF - DD800CD9)
# Daily Updated Beryl (and related projects) Packages...
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn

# Ubuntu edgy
deb http://ubuntu.uni-klu.ac.at/ubuntu/ edgy main restricted universe multiverse
deb-src http://ubuntu.uni-klu.ac.at/ubuntu/ edgy main restricted universe multiverse

# Ubuntu edgy updates
deb http://ubuntu.uni-klu.ac.at/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://ubuntu.uni-klu.ac.at/ubuntu/ edgy-updates main restricted universe multiverse

# Ubuntu edgy backports
# deb http://ubuntu.uni-klu.ac.at/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://ubuntu.uni-klu.ac.at/ubuntu/ edgy-backports main restricted universe multiverse

# Ubuntu edgy security fixes
deb http://ubuntu.uni-klu.ac.at/ubuntu/ edgy-security main restricted universe multiverse
deb-src http://ubuntu.uni-klu.ac.at/ubuntu/ edgy-security main restricted universe multiverse

deb http://ubuntu.beryl-project.org edgy main

## E17 repository "edevelop.org"
deb http://edevelop.org/pkg-e/ubuntu edgy e17
deb-src http://edevelop.org/pkg-e/ubuntu edgy e17

deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable
deb http://javadesktop.org/lg3d/debian stable contrib

```

Am I not seeing it?  I am going to restart the computer and try again.

---

### Post by Kateikyoushi on 2007-02-27
One is still in under the automatix repos.

---

### Post by dolphinsonar on 2007-02-27
Deleted automatix repros and tried apt-get install synaptic.  Got this:

```
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate

```

---

### Post by dolphinsonar on 2007-02-27
I think archive.ubuntu.com is broken.  Nothing happens when I go there in a web browser, same reaction from apt-get update.

What is an appropriate alternative to archive.ubuntu.com (us.archive.ubuntu.com does not work either).

I would need something ( a mirror? ) that has the exact same file system, but is hosted somewhere else.

Cheers!

---

### Post by Kateikyoushi on 2007-02-27
That's strange because it works for me. Try the dk.archive.ubuntu.com or one with uk.

---

### Post by dolphinsonar on 2007-02-27
OK, just doing this for the next person suffering this issue.

I went to the website:  [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

and selected that I live in Canada ( I really live in the USA), so far so good.  I pasted the output of that website into my sources.list file.  It seems to be doing something now.  Here is the new sources.list:

```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://ca.archive.ubuntu.com/ubuntu edgy main restricted 
deb http://ca.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://ca.archive.ubuntu.com/ubuntu edgy universe multiverse 
deb http://ca.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse

```

God bless Canada!  Someday I will come to you if Bush tries to draft me, and I hope your motherland is as welcoming as your sources.list!

---

### Post by Tanker Bob on 2007-03-11
dolphinsonar,

Thanks for posting your fix!  I haven't been able to connect to ubuntu.archive.com is weeks.  I went to your link, created a list for Canada, and now I'm updating with no problem.  Still don't know what the deal is with the US servers, though.

---

### Post by dolphinsonar on 2007-03-11
Great!  I am glad it worked for someone else too.  Perhaps the issue is deeper than the servers being down, but this works as far as getting synaptic back online.

Its about as technical as I can do, for now.

---

