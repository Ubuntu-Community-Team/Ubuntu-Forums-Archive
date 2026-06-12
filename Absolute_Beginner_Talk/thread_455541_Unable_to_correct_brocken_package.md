---
title: "Unable to correct brocken package"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-05-26
When I select Applications > add/remove programs I get this message.

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'

I enter sudo apt-get install -f   and runs fine then asks me if I want to continue.  Then I get this message.

Do you want to continue [Y/n]? y
(Reading database ... 127950 files and directories currently installed.)
Unpacking ardour (from .../ardour_1%3a2.0-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in package ardour-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
icu@icu-desktop:~$ 

So I rebooted and selected the second choice recovery

Some processes fail and it asks me to enter the root password for maintenance.  I enter the password it it comes back with

icu@icu-desktop:~$~#

I don't know what it is asking for here.

---

### Post by taurus on 2007-05-26
How about

```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```
Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by ICUR2Ys on 2007-05-26
Thank you.

I entered the first three commands and got this.

The following packages have unmet dependencies:
  ubuntustudio-audio: Depends: ardour but it is not installable

This is the source list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
icu@icu-desktop:~$

---

### Post by ramjet_1953 on 2007-05-27
Sometimes, Synaptic can be quite a pain, when you have a rogue install that has gone wrong.

If you have tried everything else, a last resort is this.

1. Backup your [COLOR="Blue"]/var/lib/dpkg/status[/COLOR] file  NB You MUST do this first, becuase if you lose this file, your system is hosed.

2. In a terminal, type in the following command: [COLOR="Red"]sudo gedit /var/lib/dpkg/status[/COLOR]

3. The errant package seems to [COLOR="Blue"]ardour[/COLOR], is this correct? If so, do a search for it in the opened file.

4. When you have located it, [COLOR="Red"]CAREFULLY[/COLOR] delete all references to it.

5. Save the file and re-boot.

Hopefully, all should go well, as Synaptic is no longer aware of this package and although it hasn't actually been deleted, over time, it will be over-written.

Regards,
Roger :cool:

---

### Post by tripolitan on 2007-05-27
Thanks! it solved my problem too.

---

### Post by ICUR2Ys on 2007-05-27
Thanks
I appreciate the help

---

### Post by labinnsw on 2008-03-13
Thanks,

The first problem that took less than 5 minutes to solve thanks to this post.

---

