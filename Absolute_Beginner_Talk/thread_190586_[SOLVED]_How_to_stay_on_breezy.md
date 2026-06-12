---
title: "[SOLVED] How to stay on breezy"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by TheApe on 2006-06-06
Hi all!
I really want to upgrade to Dapper, but I can't do it right now. Since I have lot of work to do, and I can't stop. Besides I'm afried to loose my data, and can't backup right now.
After I finish my stuff I want to do a clean install of dapper.
But, until there I want to know how to keep breezy updated.

I cant do ```
apt-get update
``` right now 'cause the sources aren't acessible. 

**What should I do? Change every thing in the source list from "breezy" to "dapper"? Will that dammage my installed programs?**

I can't upgrade right now, but want my distro updated.
:-k

---

### Post by nikolokolus on 2006-06-06
you will need to do 'sudo apt-get update' to bring all of your packages up to date

then do 'sudo apt-get dist-upgrade' and it will handle the rest. (there will be some interaction with the upgrade process, so it's not a complete "set and forget" procedure)

---

### Post by cstudent on 2006-06-06
If you want to keep Breezy you do not want to change your sources.list. Leave your Breezy sources.list alone and continue to update as normal.

---

### Post by TheApe on 2006-06-06
I think I didn't expressed my self well...
When I try to download something, for example "gftp".

```

sudo apt-get install gftp
Reading package lists... Done
Building dependency tree... Done
Package gftp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://wine.lowvoice.nl breezy/main Packages (/var/lib/apt/lists/wine.lowvoice.nl_apt_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://deb.opera.com etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://kubuntu.org breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://wine.lowvoice.nl breezy/main Packages (/var/lib/apt/lists/wine.lowvoice.nl_apt_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://deb.opera.com etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://kubuntu.org breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package gftp has no installation candidate

```

Ok, I give a try to apt-get update and then....
```

sudo apt-get update
Err http://kubuntu.org breezy Release.gpg
  Temporary failure resolving 'kubuntu.org'
Err http://deb.opera.com etch Release.gpg
  Temporary failure resolving 'deb.opera.com'
Err http://wine.lowvoice.nl breezy Release.gpg
  Temporary failure resolving 'wine.lowvoice.nl'
Err http://archive.ubuntu.com breezy Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err http://security.ubuntu.com breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://archive.ubuntu.com breezy-updates Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err http://archive.ubuntu.com breezy-backports Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://wine.lowvoice.nl/apt/dists/breezy/Release.gpg  Temporary failure resolving 'wine.lowvoice.nl'
Failed to fetch http://deb.opera.com/opera/dists/etch/Release.gpg  Temporary failure resolving 'deb.opera.com'
Failed to fetch http://kubuntu.org/packages/kde351/dists/breezy/Release.gpg  Temporary failure resolving 'kubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg  Temporary failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://wine.lowvoice.nl breezy/main Packages (/var/lib/apt/lists/wine.lowvoice.nl_apt_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://deb.opera.com etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://kubuntu.org breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

so, I can't use apt....
What is wrong? ](*,)

---

### Post by richbarna on 2006-06-06
I think you need to check your sources.list just in case.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
Here is a fresh one if you need it.

> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse



---

### Post by TheApe on 2006-06-06
Thanks for your help!
I replaced my sources.list with your list. But it didn't work.
It looks like I have some connection problem... apt can't find the sources...

I'm not behind a proxy... I've already downloaded software by apt-get.
What would it be the problem?

thanks

---

### Post by SuperMike on 2006-06-06
After replacing sources.list in /etc/apt dir, do this:

apt-get update

Perhaps that can fix you. If not, then the question is -- did you somehow download soemthing from the "universe", "multiverse", or "backports" option, then **upgrade when prompted after doing that**? If so, ooh - that can cause problems. It can take you into community-supported (near beta) territory and can cause problems like this. Instead, when I use an app that I can only retrieve from universe, multiverse, or backports option, I enable it, do apt-get update, _ignore_ the popup warning about doing an update, retrieve my app with apt-get install <whatever>, and then return my sources.list _without_ the universe, multiverse, and backports option, then do another apt-get update. This keeps my system fairly stable and more like what the original Ubuntu developers intended with the exception that I get the app that I wanted.

---

### Post by TheApe on 2006-06-06
There was an DNS problem....
I changed resolv.conf and it works.
LoL ](*,)

---

