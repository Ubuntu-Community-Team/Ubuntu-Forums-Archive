---
title: "still synaptic error: help me"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2006-02-13
**i've still this problem when i run synaptic:**

W: Impossible to check the source packages list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages listte [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages listte [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to check the source packages list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

**i've changed the /etc/atp/souces.list as advised in this forum :**

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
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
## team

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## official backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH [http://ovh.com](http://ovh.com)
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## plf secondary repo. Use if primary repo is offline.
## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
## deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
## deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

## plf mirror. Use if primary and secondary are offline
## deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

## opera web browser
## deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

[B]then i ran: sudo apt-get update ; sudo apt-get upgrade

every time i switch on the pc i find this problem and i tried many different version of souces.list without solving it. 

To solve the problem i've each time to download the repositary universe. I got a 56k modem and this is stressing me.

After the "sudo apt-get update ; sudo apt-get upgrade" every time it works well, but if i switch off the pc the the story
starts againg.

Now i've just switched on the pc , the message error is posted above; i check the /var/lib/apt/lists: inside there is a file called
lock and a directory called partial with inside:

/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_breezy-backports_Release.gpg
/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_breezy_Release.gpg
/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_breezy-updates_Release.gpg
/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_breezy-security_Release.gpg

please help me
:cry: [/B]

---

### Post by TeeAhr1 on 2006-02-13
How long has this been going on?  I just reinstalled last week, and I was also having major issues getting to archive.ubuntu.com.  Then, Saturday morning, everything magically worked when I changed sources.list back to *its original state*, plus my extra repositories.

Sorry, I don't have a solution for you, but I just wanted to poke my head up in solidarity.  That's the worst thing to break, too, because you're crippled until it's fixed.  Good luck, keep us posted.

---

### Post by wolfmaniac on 2006-02-13
run get-update in terminal as root

---

### Post by wolfmaniac on 2006-02-13
juz take a backup

Q: How to backup/restore downloaded repositories cache?

   1. Read General Notes
   2. To backup downloaded repositories cache

sudo tar zcvf apt.tgz /etc/apt/ /var/lib/apt/ /var/cache/apt/

   3. To restore downloaded repositories cache

sudo tar zxvf apt.tgz -C /

---

### Post by wolfmaniac on 2006-02-13
Q: How to download this entire UbuntuGuide?

   1. Read General Notes
   2.

wget -c [http://ubuntuguide.org/YET](http://ubuntuguide.org/YET) TO GET IT DONE
 tar zxvf ubuntu5.10.tar.gz

---

### Post by ubunlilluz on 2006-02-21
i tried to clean the archive by 
apt-get clean

and then download everything again.
it worked always only for the current session, then all things
were in the archives had been canceled. Canceled, but i don't know why and by who.
Help

---

