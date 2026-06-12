---
title: "[SOLVED] Synaptic problem"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2007-12-09
Came home today and found that there were updates. Tried to see what they were and got this error:

> Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing qterm (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Tried Add Remove Programs and got this:

> Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Here is the output of ```
cat /etc/apt/sources.list

``` since im sure you will all ask me to post it:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by PmDematagoda on 2007-12-09
Open the sources.list file for editing using:-

```
sudo gedit /etc/apt/sources.list
```

Then uncomment the repositories by removing the # in front of them, such as:-

```
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
```

Should look like this:-

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
```

After making the necessary changes, save the file and then do:-
```

sudo apt-get update
```

That should fix your problem.

---

### Post by rsambuca on 2007-12-09
Why will activating the backports repository fix this?

---

### Post by PmDematagoda on 2007-12-09
Good point rsambuca, I did not read the post thoroughly, sorry bladefallcon, activating the backport repos will not fix it.

Since the issue is with a package list, why don't you try:-
```

sudo apt-get update
```

---

### Post by Partyboi2 on 2007-12-09
try in a terminal
```
sudo apt-get install -f
```

---

### Post by bladefallcon on 2007-12-09
Both ```
Sudo apt-get install 0f
```
and ```
sudo apt-get update
```

give me the following error:

```
E: Problem parsing dependency Depends
E: Error occurred while processing qterm (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

---

### Post by PmDematagoda on 2007-12-09
Remove the list file using:-
```

sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages
```

Then try:-

```
sudo apt-get update
```

---

### Post by bladefallcon on 2007-12-09
That seems to have worked...thank you.

---

### Post by PmDematagoda on 2007-12-09
Glad it worked out:).

---

### Post by trebor on 2007-12-31
I have a similar problem with Edgy.  My synaptic gives me this fault.

 The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

Here is my sources list.

# Major bug fix updates produced after the final release of the
# distribution.
# Use the following sources.list at your own risk.
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#  If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties


# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse


# Seveas' Ubuntu Packages
# GPG key: 1135D466
# deb-src [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) edgy-seveas all
# deb-src [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas all


# Kubuntu.org bleeding edge Koffice
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) edgy main

# Upstream Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

# bzr nightly snapshots
# deb [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

# deb-src [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

# Upstream Beryl
# GPG key: ed8a569e
# deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy

# deb-src [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy

# Medibuntu multimedia packages
# GPG key: 0C5A2783
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main
deb-src [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main multiverse universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe 

Thanks for help in advance.

---

### Post by PmDematagoda on 2007-12-31
Try changing the location of the servers in System>Administration>Software Sources, then run:-
```
sudo apt-get update
```

---

