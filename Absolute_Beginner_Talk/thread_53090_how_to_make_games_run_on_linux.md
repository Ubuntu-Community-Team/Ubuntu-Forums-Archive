---
title: "how to make games run on linux"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by playmate19 on 2005-07-30
okay i am looking for how to run windows games on linux 
i am using ubuntu and i am blonde
i have master how to use the root terminal (command line i believe it is)
and i just want to know what i can do to make them run and playable

please help me out 

thanks guys

---

### Post by adwait on 2005-07-30
Hi,

Well, it may not be possible to run all the games on Linux. But, many can be run using a software known as wine (WINdows Emulator). First you need to install it using

```
sudo apt-get install wine
```

After that....you can try to run the game you want from the command line using

```
wine /game/path 
```

---

### Post by drummer on 2005-07-30
Native Linux games:
[http://ubuntuforums.org/showthread.php?t=5153](http://ubuntuforums.org/showthread.php?t=5153)

Native Windows games under Linux using Cedega:
[http://www.transgaming.com/products_linux.php](http://www.transgaming.com/products_linux.php)

---

### Post by playmate19 on 2005-07-30
okay so i download the game 
how do i install it thats the thing do i use that path and put the install name

---

### Post by zappa86 on 2005-07-31
[QUOTE=adwait]Hi,

Well, it may not be possible to run all the games on Linux. But, many can be run using a software known as wine (WINdows Emulator). First you need to install it using

```
sudo apt-get install wine
```

After that....you can try to run the game you want from the command line using

```
wine /game/path 
```[/QUOTE]


When I do apt-get install wine
It says:

Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

---

### Post by drummer on 2005-07-31
have you enabled the 'universe' repository? ( [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) )
Wine is in Universe, there shouldn't be a problem installing wine if Universe is enabled.

---

### Post by playmate19 on 2005-07-31
the wine program installed alright

---

### Post by kahping on 2005-07-31
[QUOTE=adwait]... But, many can be run using a software known as wine (WINdows Emulator). ...[/QUOTE]

some people prefer "Wine Is Not an Emulator" ;-)

kahping

---

### Post by Semper9599 on 2005-07-31
I did all this and it did not work i have an amd 64 all i got was this
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package wine has no installation candidate

---

### Post by adwait on 2005-07-31
As mentioned above, enable universe in your repositories.

---

### Post by kvidell on 2005-07-31
> **kahping]some people prefer "Wine Is Not an Emulator"  said:**
> 
 You mean like the people who wrote it? ^.^

From the WINE Faq:
[quote]2.2. Does Wine emulate a full computer?

No, as the name says, **W**ine **I**s **N**ot an **E**mulator
God I hate recursive acronyms.
- Kev

---

### Post by Semper9599 on 2005-08-01
ok i did all this and the stuff on the link how do i find out if it is on my pc

---

### Post by adwait on 2005-08-01
type the command
```
wine
```

What happens? If it says command not found or something, it means it isnt installed.if not, it is.

---

### Post by 1veedo on 2005-10-24
I ahve the same error messages:> W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)I did everything the ubuntuguide said.  I think the repositories are only for 32 bit because it complains about 64.

---

### Post by Ampersand on 2005-10-24
The ubuntu-backports.mirrormax.net servers are no longer active, so those should be removed from your sources.list. I'm not sure about the other servers it's got errors about, if they still exist a 'sudo apt-get update' should solve the problem.

---

