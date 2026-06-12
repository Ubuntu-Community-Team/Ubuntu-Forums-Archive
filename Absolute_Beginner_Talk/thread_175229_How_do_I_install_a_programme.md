---
title: "How do I install a programme"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by clemkonan on 2006-05-13
I need to install a text to speech replacement for Please Read which runs under Windows. I found a package called Festival, how do I install it under Ubantu.

Also is there a good book or tutorial on Ubantu linux
Sincere  thanks

---

### Post by richbarna on 2006-05-13
Hi clemkonan, it's ubUntu :)

To install festival (and all other programs):-
1. Open the console
2. Type :- sudo apt-get install festival (and click enter)
3. Type in your password (and click enter again)
4. Hey presto !! downloaded and installed.

Ubuntu help and info :- [http://ubuntuforums.org/showthread.php?t=142716]("http://ubuntuforums.org/showthread.php?t=142716")

Any problems, let us know.
Good luck !!

---

### Post by aysiu on 2006-05-13
richbarna's instructions are good.

For more on how to install applications, read these two links:
[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by clemkonan on 2006-05-13
Typing sudo apt-get install festival returned  a message that the programme was not found. Using synaptic manager , the seach box returns Festival on the big box on the left but no files are displayed and there is nothing to click on.  I get some thine " ALL" then below it "Festival" and a mesage no file selected. I even tried searching for  AVG  the ubiquitous anti virus and still no luck.
The files I need are:
    * festival-1.95-beta.tar.gz -- The core festival package
    * speech_tools-1.2.95-beta.tar.gz -- The Edinburgh Speech tools library
    * festlex_OALD.tar.gz -- The lexicon distribution
    * festlex_POSLEX.tar.gz -- The lexicon distribution
    * festvox_rablpc16k.tar.gz -- The speech database
The download page is [http://software.newsforge.com/article.pl?sid=05/06/14/192226&from=rss](http://software.newsforge.com/article.pl?sid=05/06/14/192226&from=rss)

This is a programme that converts test to speech. gues I still need a bit more help. Yes, I have been reading through those excellent links above

---

### Post by richbarna on 2006-05-14
Ok, it is there because i've checked.
You may have to change your sources.list file.
Open the console and type :- 
(oh by the way gedit, kate, vim are text editors, I use vim)
> sudo gedit /etc/apt/sources.list

It should look like this :-
> eb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

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
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free



If you have a look at yours, and you see that there are #'s in front of any of the repository URL's, you have to delete them.

If you like, you can delete everything, and just copy and paste mine in it's place.

---

### Post by clemkonan on 2006-05-16
Just a quick reply to say I have been travelling so I have not been able to follow up; however I will do so and post back. Thanks for all the great info.

---

### Post by clemkonan on 2006-05-16
Here is what that line pasted into Terminal gave me. I assume by console you mean Terminal
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by clemkonan on 2006-05-16
I pasted your output, saved, re-booted and got this:
clem@ubuntuhurricane:~$ sudo apt-get install festival
Password:
E: Type 'eb-src' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
clem@ubuntuhurricane:~$

---

### Post by aysiu on 2006-05-16
richbarna left off the *d* at the beginning of the first line... It should be *deb-src*, not *eb-src*. [QUOTE=richbarna]
It should look like this: ```
**eb-src** http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/ breezy free non-free
```[/QUOTE]

---

### Post by clemkonan on 2006-05-18
I know perseverence will be rewared so I press on.  I changed the line but as you can see below there is still a minor problem:
clem@ubuntuhurricane:~$ sudo apt-get install festival
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package festival
clem@ubuntuhurricane:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
clem@ubuntuhurricane:~$

---

### Post by dmizer on 2006-05-18
no problem ...

apt-get is a program that needs to run with root permissions.  so all you have to do is type "sudo" in front of apt-get.  like so:
```
sudo apt-get update
```
it will prompt you for your password, and then it will update.

after that, you can install your software (again: sudo apt-get ...)

here's a bit more information about sudo if you're interested:
[https://wiki.ubuntu.com/RootSudo?action=show&redirect=Sudo](https://wiki.ubuntu.com/RootSudo?action=show&redirect=Sudo)

---

### Post by clemkonan on 2006-05-19
Update reported some items not updated or old copies used. Tried to install Festival looks like some debugging is still required.
clem@ubuntuhurricane:~$ sudo apt-get install festival
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  festlex-cmu festlex-poslex festvox-kallpc16k libestools1.2
The following NEW packages will be installed:
  festival festlex-cmu festlex-poslex festvox-kallpc16k libestools1.2
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 7375kB of archives.
After unpacking 20.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main libestools1.2 1:1.2.3-9 [1384kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main festlex-poslex 1.4.0-5 [235kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main festlex-cmu 1.4.0-6 [881kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main festvox-kallpc16k 1.4.0-5 [4094kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main festival 1.4.3-17ubuntu1 [782kB]
Fetched 7375kB in 15s (466kB/s)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

Preconfiguring packages ...
Selecting previously deselected package libestools1.2.
(Reading database ... 61297 files and directories currently installed.)
Unpacking libestools1.2 (from .../libestools1.2_1%3a1.2.3-9_i386.deb) ...
Selecting previously deselected package festlex-poslex.
Unpacking festlex-poslex (from .../festlex-poslex_1.4.0-5_all.deb) ...
Selecting previously deselected package festlex-cmu.
Unpacking festlex-cmu (from .../festlex-cmu_1.4.0-6_all.deb) ...
Selecting previously deselected package festvox-kallpc16k.
Unpacking festvox-kallpc16k (from .../festvox-kallpc16k_1.4.0-5_all.deb) ...
Selecting previously deselected package festival.
Unpacking festival (from .../festival_1.4.3-17ubuntu1_i386.deb) ...
Setting up libestools1.2 (1.2.3-9) ...

Setting up festlex-poslex (1.4.0-5) ...
Setting up festvox-kallpc16k (1.4.0-5) ...
Setting up festival (1.4.3-17ubuntu1) ...

Setting up festlex-cmu (1.4.0-6) ...
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5f...lf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
clem@ubuntuhurricane:~$

---

### Post by user1397 on 2006-05-19
clemkonan, have you tried typing:
```
sudo apt-get update
```
before you install the program?

---

### Post by clemkonan on 2006-05-19
Actually, yes I did here is the code. See the last 2 lines:
clem@ubuntuhurricane:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Get:7 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [60.2kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [39.0kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [17.3kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [35.0kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [18.6kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Get:20 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources [5185B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources [14B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources [10.2kB]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources [701B]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:28 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:29 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:30 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:31 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Get:32 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
  Unable to fetch file, server said 'Failed to open file.  '
Get:33 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
  Unable to fetch file, server said 'Failed to open file.  '
Get:34 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:35 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
  Unable to fetch file, server said 'Failed to open file.  '
Fetched 316kB in 6s (49.9kB/s)
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/breezy/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/breezy/free/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
clem@ubuntuhurricane:~$

---

### Post by dmizer on 2006-05-19
[QUOTE=clemkonan]W: You may want to run apt-get update to correct these problems
clem@ubuntuhurricane:~$[/QUOTE]
there's your answer.  if you get errors when you do apt-get update, it will tell you to run update again.  sometimes this happens because a repository didn't respond when quired, just run apt-get update again until you don't get the error.

---

### Post by dmizer on 2006-05-19
okay ... your repository is messed up somehow.

do this:
```
gksudo gedit /etc/apt/sources.list
```
delete everything that is in the file, and replace it with this:
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
```

---

### Post by macdo on 2006-05-19
Festival is installed, though...
[quote=clemkonan]```
Setting up libestools1.2 (1.2.3-9) ...

Setting up festlex-poslex (1.4.0-5) ...
Setting up festvox-kallpc16k (1.4.0-5) ...
Setting up festival (1.4.3-17ubuntu1) ...

Setting up festlex-cmu (1.4.0-6) ...
```[/quote]

---

### Post by clemkonan on 2006-05-19
Now I am relly worried. Using this command and my password the source list came up empty, a blank nothing there. I exited without saving and got this. By the way the command was entered into Terminal.
(gedit:15646): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
clem@ubuntuhurricane:~$

---

### Post by clemkonan on 2006-05-19
Hello macdo, I was actually into the process of getting the download as you can see below
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main libestools1.2 1:1.2.3-9 [1384kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main festlex-poslex 1.4.0-5 [235kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main festlex-cmu 1.4.0-6 [881kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main festvox-kallpc16k 1.4.0-5 [4094kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main festival 1.4.3-17ubuntu1 [782kB]
I entered a "y" at the Y/N prompt but I guess I should have entered the "Get" command listed for each line is that correct?

---

### Post by clemkonan on 2006-05-19
Does this not mean I have the download just need to know what to do next?

clem@ubuntuhurricane:~$ sudo apt-get install festival
Reading package lists... Done
Building dependency tree... Done
festival is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
clem@ubuntuhurricane:~$

---

### Post by macdo on 2006-05-19
Just press alt+F2, and type in "festival" (without the quotes).
Or you can look for it in your application menu.
Apt-get downloads and installs programs for you. It's not like Windows, where you download then install.

---

### Post by clemkonan on 2006-05-19
Ok, I used applications | add programmes and installed it. Now what is the equivalent of a startup Icon or system tray so that I can see and alunch my programme

---

### Post by 3rdalbum on 2006-05-20
Typing the name of the program into the terminal will probably start it up. If it doesn't, try typing "man *programname*", which brings up a manual of the program. (substitute the word "programname" for the name of your program)

Some programs don't add themselves to the Applications menu, but the good news is that Ubuntu allows you to add them yourself. Go to Applications > System Tools > Applications Menu Editor. Click on the category you want the program to be in, click the New Entry button, and type a name and comment for it. In the "command" field, type the actual application name - the terminal command that launches the program.

You can click OK here, or select an icon for the menu item. If you launch the program and it doesn't do anything, try editing that menu item so that the "Run in Terminal" box is checked.

---

### Post by richbarna on 2006-05-20
[QUOTE=aysiu]richbarna left off the *d* at the beginning of the first line... It should be *deb-src*, not *eb-src*.[/QUOTE]

Actually I missed it when I copy and pasted (highlighted with mouse) ](*,) 
Silly me ]:rolleyes:

Sorry clemkonan,

---

### Post by clemkonan on 2006-05-20
Not a problem richbarna, all the help is appreciated I can't wait to say goodbye to Microsoft. The learning curve is steep but I have 3 computers so it will pay off handsomely.

---

### Post by clemkonan on 2006-05-21
I am getting a bit mixed up with this one. 
Some programs don't add themselves to the Applications menu, but the good news is that Ubuntu allows you to add them yourself. Go to Applications > System Tools > Applications Menu Editor. Click on the category you want the program to be in, click the New Entry button, and type a name and comment for it. In the "command" field, type the actual application name - the terminal command that launches the program.

You can click OK here, or select an icon for the menu item. If you launch the program and it doesn't do anything, try editing that menu item so that the "Run in Terminal" box is checked.
I chose office | new  then I entered festival as the name. Now I need a "comment" and a "command". I am not clear what to use for either.  An example would help. 
Once again thanks for your patience.

---

### Post by richbarna on 2006-05-21
RE:- Comment /Command are the same as when you right click the desktop to create a shortcut.
Program   :- Firefox
Comment :- Web Browser (optional info)
Command :- user/bin/firefox (usually whare and what program it should open)

---

### Post by macdo on 2006-05-21
In your case:

Name: Festival
Comment: A text-to-speech app. (you can put in anything you like here)
Command: festival

---

### Post by clemkonan on 2006-05-21
Looks like I have messed things up. My top toolbar : Applications| Places| System| Browser | Mail, etc has a yellow triange with a question mark and next to the system tray close to the time  and sound icon ( far right hand side)  is an new icon. the Triangel  reads " kttsmgr KDE speech to test manager and the icon reads " spech to test manager".
Right clicking on the yellow triangle I see " Launch, properties, remove from panel, etc" for th other icon righ clicking gives : Kttsmgr, speech clipboard content, KTTS handbook, about KTSSmgr, Quit, restore.
Looks like it all these just to be configured.

Clicking Launch does not work so my comments from my last message still holds.

---

### Post by clemkonan on 2006-05-21
ok, I am following up on the last two messages will fix the comment and command and get back to you momentarily

---

### Post by clemkonan on 2006-05-21
The yellow triangle icon with a ? mark and Office both execute a a launch in terminal that identiifies the programme version, university source, etc but that all. I have an error in office , 2 copies of festival , one uses user/ bin / festival, the other for a command simply uses festival. 
I need to delete the two icons in office and try again. The second icon on the right by my audio icon is gone ( after reboot) . system is starting to act buggy hard to post.

---

