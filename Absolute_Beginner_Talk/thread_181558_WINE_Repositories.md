---
title: "WINE Repositories"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by joshbax on 2006-05-24
Hey,

I want to install WINE and I have followed the instructions on the WINE site to install it with synaptic.

But it seems I cannot connect to the repository.

I get the following screen:

[[IMG]http://img394.imageshack.us/img394/3258/screenshot7gr.th.png[/IMG]](http://img394.imageshack.us/my.php?image=screenshot7gr.png)

Any advice guys?

Thanks.

---

### Post by ronlybonly on 2006-05-24
joshbax, I am running Dapper, but these steps should still work for Breezy.

1.) Open your sources.list file by typing the following at a command line: sudo gedit /etc/apt/sources.list
2.) Uncomment the line that reads "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe"
3.) Comment the line that refers to the WINE repository (it will read something like "deb http://wine.budgetdedicated.com...")
4.) Save the changes to sources.list, and exit gedit.
5.) From the command line, type "sudo apt-get update"
6.) Finally, type "sudo apt-get install wine"

That should do it for you. Let me know if you are still having problems.

-Andy

---

### Post by sYs^ on 2006-05-24
Or try this repo:
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

---

### Post by joshbax on 2006-05-24
ronlybonly, i just tried that stuff, and got this

```
josh@HAL-9000Linux:~$ sudo gedit /etc/apt/sources.list
Password:
josh@HAL-9000Linux:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package wine has no installation candidate

```

this is what my sources.list file looks like

> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main


sYs, I aint too good with binary, but will try that. Thanks!

---

### Post by joshbax on 2006-05-25
bump

---

