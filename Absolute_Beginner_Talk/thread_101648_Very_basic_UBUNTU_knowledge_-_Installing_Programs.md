---
title: "Very basic UBUNTU knowledge - Installing Programs"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by olieviya on 2005-12-10
I need serious help. I have no idea how to install programs!

I've downloaded ClamAV and have no idea what to do with it, it seems like a kind of archive file that i can view but I can't see any file called install and when I try to paste it somewhere else it says permission denied.

I've gathered that what I have to do is get onto a command line interface and start giving it some basic commands, right? I have no idea please help!

---

### Post by Gustav on 2005-12-10
Most programs are easely downloaded and installed trough the synaptic package manager (System->Administration->Synaptic Package Manager)

---

### Post by mcduck on 2005-12-10
Just open synaptic, click 'search' and type 'clamav'.

or you can use terminal ('command line') in Application/Accessories and enter command 'sudo apt-get install clamav'

---

### Post by olieviya on 2005-12-10
I've got the Synaptic thingie open right now, I clicked search "clamav" and nothing came up, I then clicked reload and a pop up came up called "Downloading package information" and it's downloading stuff - it's taking a long time to download stuff. I clicked the "Show progress of single files" but most of them seem to be Status:Failed.

What's going on?

---

### Post by olieviya on 2005-12-10
It's also telling me that the following problems have been found on my system:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Rackerz on 2005-12-10
Don't mind those errors, they don't mean anything apprently. I get them and no problems. What kind of file is it? .deb? .rpm? .tar.gz?

Darren

---

### Post by ssam on 2005-12-10
those errors should go away once you have clicked the reload button.

if you can't find clamav, it might be in the universe repository, see [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) , then search again

---

### Post by olieviya on 2005-12-10
It's a tar.gz

---

### Post by olieviya on 2005-12-10
I'm having a spot of trouble when I click the reload button, it takes a-g-e-s when it gets to the 11th package and I'm on DSL. Shall I just leave it for a while?

---

### Post by atoponce on 2005-12-10
If you have already downloaded the tar.gz, then installing it is a bit more difficult than Synaptic, but can be accomplished nonetheless.

Open up a terminal and type (replace <name_of_clamav_file> with the actual file name):

```
tar zxvf <name_of_clamav_file>.tar.gz
cd <name_of_clamav_file>
ls
```

If you have a binary, it will show up in green (probably named install or something similar), at which case you would do:

```
./<name_of_binary>
```

However, I bet this isn't the case, and as such you will have to compile and make the program yourself:

```
./configure
make
sudo make install
sudo make clean
```

That should be it!

---

### Post by olieviya on 2005-12-10
How do you open up a terminal?

---

### Post by atoponce on 2005-12-10
If you are running Breezy 5.10, go to

Applications -> Accessories -> Terminal

---

### Post by linbetwin on 2005-12-10
Applications > Accessories > Terminal.

---

### Post by olieviya on 2005-12-10
Thanks a lot - I will try the things you suggested now!

---

### Post by olieviya on 2005-12-10
What am I doing wrong?

olivia@BOB:~$ tar zxvf /home/olivia/Desktop/clamav-o.87.1.tar.gz
tar: /home/olivia/Desktop/clamav-o.87.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
olivia@BOB:~$

---

### Post by Rackerz on 2005-12-10
I think the file name is wrong, try copying and pasting.

---

### Post by olieviya on 2005-12-10
Is this it?

olivia@BOB:~$ cd /home/olivia/Desktop/clamav-0.87.1
olivia@BOB:~/Desktop/clamav-0.87.1$ ls
acinclude.m4        clamd         COPYING    INSTALL          mkinstalldirs
aclocal.m4          clamdscan     database   install-sh       NEWS
AUTHORS             clamscan      depcomp    libclamav        README
BUGS                config.guess  docs       libclamav.pc.in  shared
ChangeLog           config.sub    etc        ltmain.sh        sigtool
clamav-config.h.in  configure     examples   Makefile.am      test
clamav-config.in    configure.in  FAQ        Makefile.in      TODO
clamav-milter       contrib       freshclam  missing          UPGRADE
olivia@BOB:~/Desktop/clamav-0.87.1$

---

### Post by Rackerz on 2005-12-10
Im not sure what all that means, is there any indication in your applications menu that it's been installed? If not what files are inside clamav-0.87.1.

---

### Post by aysiu on 2005-12-10
There's absolutely no reason you should have to install from source (.tar.gz)

Your repositories aren't up to date if you don't have ClamAV. See the first link in my sig. Then install it through Synaptic.

You may also want to read: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by Rackerz on 2005-12-10
[QUOTE=aysiu]There's absolutely no reason you should have to install from source (.tar.gz)

Your repositories aren't up to date if you don't have ClamAV. See the first link in my sig. Then install it through Synaptic.

You may also want to read: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)[/QUOTE]

Do exactly this. I missed this because im in Windows. My apologies.

---

### Post by Danielle on 2005-12-10
when you have updated your repositories you should be able to find clamtk there which is a frontend for F-Prot

---

### Post by olieviya on 2005-12-10
No indication - nothing. It contains many many folders that in turn contain files with extensions .c, .am, .in, .h, .conf ...etc

---

### Post by olieviya on 2005-12-10
No luck there at all...

olivia@BOB:~$  sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
olivia@BOB:~$ sudo gedit /etc/apt/sources.list

olivia@BOB:~$
olivia@BOB:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.151), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.151), connection timed out
0% [Connecting to archive.ubuntu.com (82.211.81.151)]

etc etc etc

---

### Post by olieviya on 2005-12-10
Thing is I can't seem to manage to do that right now...

---

### Post by aysiu on 2005-12-10
[QUOTE=olieviya]connection timed out[/QUOTE] I've seen this problem before. [This](http://www.ubuntuforums.org/showthread.php?t=95440) might help.

---

### Post by olieviya on 2005-12-11
I will try what you said - thanks.

The errors I'm getting now are:

1.
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

2.
The following problems were found on your system:
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


3.
The following problems were found on your system:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by olieviya on 2005-12-11
Thanks a lot everyone, I have finally managed to fix the problem!!

;)

---

### Post by aysiu on 2005-12-11
[QUOTE=olieviya]Thanks a lot everyone, I have finally managed to fix the problem!!

;)[/QUOTE] How did you do it? I'm just wondering in case anyone else has this problem, does a forum search, and stumbles upon this thread.

---

### Post by olieviya on 2005-12-11
I followed the instuctions on how to fix it up here: [http://ubuntuforums.org/showthread.php?t=95350&highlight=router+synaptic](http://ubuntuforums.org/showthread.php?t=95350&highlight=router+synaptic)

and also put in my dns settings

Not actually sure which one was the problem but since it works! :P

Also I restarted after all that.

By the way I don't know why but I created another thread about me having some probelm with my monitor and nobody seems to know anything (nobody has replied and so it's gone from the forum). Do you have any ides? [http://www.ubuntuforums.org/showthread.php?t=101639](http://www.ubuntuforums.org/showthread.php?t=101639)

---

### Post by olieviya on 2005-12-11
Something very weird is going on: 
I have entered my DNS setting many times but it keeps removing them replacing them with the default.
I go to System>Administration>Networking>DNS tab and fill in the three DNS Servers my ISP has but if I close the window and then reopen it they will disappear I have also tried restarting and they still go away! What is wrong?

This my ISP's DNS and other stuff info page: [http://www.spidernet.net/main/default.aspx?tabid=86](http://www.spidernet.net/main/default.aspx?tabid=86)

---

