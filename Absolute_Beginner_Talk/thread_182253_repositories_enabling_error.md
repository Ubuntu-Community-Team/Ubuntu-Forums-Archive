---
title: "repositories enabling error"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-25
i am new to ubuntu
i want to install certain applications in ubuntu
i followed the guide at wiki to enable rpositories and my results were completed 44%
following are the error messages + my commands

ejaz@ejaz:~$ sudo nano /etc/apt/sources.list
Password:
ejaz@ejaz:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak
ejaz@ejaz:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
ejaz@ejaz:~$

plz tell me what to do

---

### Post by johnc4510 on 2006-05-25
Go to this web site and look under repositories:
[http://ubuntuguide.org/](http://ubuntuguide.org/)
Follow the instructions
Note: There are many, many good things in this guide

---

### Post by aysiu on 2006-05-25
[QUOTE=johnc4510]Go to this web site and look under repositories:
[http://ubuntuguide.org/](http://ubuntuguide.org/)
Follow the instructions[/QUOTE] That guide's been obsolete for almost a year now.

Try the bottom of this page:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

If that doesn't work, try the top of the page.

---

### Post by johnc4510 on 2006-05-25
Your right, I thought it was the guide for breezy not hoary
Sorry

---

### Post by u04f061 on 2006-05-25
[QUOTE=aysiu]That guide's been obsolete for almost a year now.

Try the bottom of this page:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

If that doesn't work, try the top of the page.[/QUOTE]


the following error occured when following the link u gave

ejaz@ejaz:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo: timestamp too far in the future: May 26 11:17:05 2006
ejaz@ejaz:~$

what does this means??????????
plz tell me and fix the error if u can

---

### Post by aysiu on 2006-05-25
[QUOTE=u04f061]the following error occured when following the link u gave

ejaz@ejaz:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo: timestamp too far in the future: May 26 11:17:05 2006
ejaz@ejaz:~$

what does this means??????????
plz tell me and fix the error if u can[/QUOTE] Have you changed the time on your Ubuntu computer lately?

---

### Post by u04f061 on 2006-05-25
[QUOTE=aysiu]Have you changed the time on your Ubuntu computer lately?[/QUOTE]
yes i set the time according to my location
is this the problem the then what should i do?
it is displaying me the time when i set new time on my pc

---

### Post by Mustard on 2006-05-25
Try rebooting the computer and see if it fixes it.

---

### Post by u04f061 on 2006-05-25
[QUOTE=Mustard]Try rebooting the computer and see if it fixes it.[/QUOTE]

yes u r online now plz have a conversation with me to fix my error.
i have rebooted my pc and it went to 40% apt-get update and then follwing error message was given


ejaz@ejaz:~$ sudo apt-get update
Password:
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
ejaz@ejaz:~$

---

### Post by Mustard on 2006-05-25
Well it looks like a connection problem to the repositories.  What type of connection are you using?  Do you normally go through a proxy server?

---

### Post by u04f061 on 2006-05-25
[QUOTE=Mustard]Well it looks like a connection problem to the repositories.  What type of connection are you using?  Do you normally go through a proxy server?[/QUOTE]

i always use lan cable of 100Mb/s.
i am in university,our proxy server is also in our university.i'll go to my university shortly after one hour.if u can find some error in my proxy server plz tell me so that i may report bug there

sorry for 11 minute late

---

### Post by Mustard on 2006-05-25
I would say that apt-get and synaptic are not configured for your proxy connection. I'm just looking up a link to help you with this.

-edit-

Check this link out, go to the bottom of the page...
[https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto)

-edit-

Yeah, sorry for the delay.  I'm chatting with my girlfriend on MSN at the same time. :)

Does your connection require you to authenticate to the proxy server ie with a username and password?  If so it could be problematic to set it up without some further assistance.

---

### Post by u04f061 on 2006-05-26
[QUOTE=Mustard]I would say that apt-get and synaptic are not configured for your proxy connection. I'm just looking up a link to help you with this.

-edit-

Check this link out, go to the bottom of the page...
[https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto)

-edit-

Yeah, sorry for the delay.  I'm chatting with my girlfriend on MSN at the same time. :)

Does your connection require you to authenticate to the proxy server ie with a username and password?  If so it could be problematic to set it up without some further assistance.[/QUOTE]


thanks to u .u gave a link which worked and resolved my problem absolutely
but two line message i think is an error at the end of all updates.plz have a look at this

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by Mustard on 2006-05-26
[QUOTE=u04f061]thanks to u .u gave a link which worked and resolved my problem absolutely
but two line message i think is an error at the end of all updates.plz have a look at this

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems[/QUOTE]

The error sort of explains itself. Somewhere in your sources.list the same repository is being accessed twice.  In this case it's the universe repository.  The answer would be to either open the /etc/apt/sources.list file in an editor (using sudo to open the editor, as you are editing a system file) and find the duplicate reference yourself and remove it, or access a default copy of the sources.list for Breezy Badger and replace your old copy with a brand new default copy of the sources.list.

This is an example of my Breezy Badger sources.list that you can use if you want as your own, or use it as a reference to find the duplicate entry in your own sources.list.

```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
 deb-src http://au.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
 deb-src http://au.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://au.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://au.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

---

