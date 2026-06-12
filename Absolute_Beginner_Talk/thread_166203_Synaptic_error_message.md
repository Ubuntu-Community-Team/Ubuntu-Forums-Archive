---
title: "Synaptic error message"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-26
Out of the blue I get this error message when I load Synaptic :

W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_bina ry-i386_Packages) - stat (2 No such file or directory)

I'd be grateful for any advice as to what I should do.

---

### Post by Sef on 2006-04-26
Post the results from your /etc/apt/sources.list.

sudo gedit /etc/apt/sources.list

---

### Post by cliff0108 on 2006-04-26
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

## created by arnieamuleadded

---

### Post by professor_chaos on 2006-04-26
that error message means that at the time you updated that site/path wasn't accessable. However, I can get to that site/path now, so if you try "sudo apt-get update" and don't get the message again, then it means the first time the site wasnt available and now is. If not, then I can't say I know what the problem is.

---

### Post by cliff0108 on 2006-04-26
That worked !
Thanks so much for your help !
The best part of Ubuntu is the kindness of the folks in this forum who go out of their way to help beginners like myself !
I am definitely a convert and will do my best to pass on whatever knowlege I acquire (whenever I feel I know somthing :o) ) !

---

### Post by professor_chaos on 2006-04-26
no problem. 
Ive found that unlike other OS's, the error messages you get in Linux generally speaking have some information in them that can help you track the problem.
This forum is really a great place to ask questions and get help. Enjoy your stay here.

---

### Post by rutterhj on 2006-04-26
hello I get a similar issue when i try to enable the multiverse repositories in the Package Manager. Here is the error message I get:

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/mulitverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_mulitverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

I don't know what this means so any help would be appreciated. 

Thanks!

---

### Post by Mustard on 2006-04-27
[QUOTE=rutterhj]hello I get a similar issue when i try to enable the multiverse repositories in the Package Manager. Here is the error message I get:

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/mulitverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_mulitverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

I don't know what this means so any help would be appreciated. 

Thanks![/QUOTE]


Either hit the 'Reload' button in Synaptic Package Manager.. 

Or close Synaptic and do this command from the terminal..

```
sudo apt-get update
```

---

### Post by Melciah on 2006-04-27
im getting a similar message: 

W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

when i reload, it hangs on file 5. similarly, if i sudo apt-get update it hangs at 66%.

---

