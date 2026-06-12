---
title: "Question on Synaptic (stupid user error)"
date: 2005-03-01
forum: Apple PPC Users
---

### Post by godsunderstudy on 2005-03-01
I am a Linux newbie, eMac owner with Ubuntu Warty installed.

Synaptic Package manager worked as well as can be expected until I decided to become idiotic and change Settings -> Preferences -> Expert -> Distrobution Default Archive to Warty thinking it would help. However, now no packages at all come up and not even changing it back to ignore gets the packages back. I also get the floowing error messages (although all but the first two came up before and are probably simple 404 errors). 



```

Couldn't stat source package list cdrom://Ubuntu 4.10 _Warty Warthog_ - Preview powerpc Binary-1 (20041020) unstable/main Packages (/var/lib/apt/lists/Ubuntu%204.10%20%5fWarty%20Warthog%5f%20-%20Preview%20powerpc%20Binary-1%20(20041020)_dists_unstable_main_binary-powerpc_Packages) - stat (2 No such file or directory)
```

```
Couldn't stat source package list cdrom://Ubuntu 4.10 _Warty Warthog_ - Preview powerpc Binary-1 (20041020) unstable/restricted Packages (/var/lib/apt/lists/Ubuntu%204.10%20%5fWarty%20Warthog%5f%20-%20Preview%20powerpc%20Binary-1%20(20041020)_dists_unstable_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
```

```
Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-powerpc_Packages) - stat (2 No such file or directory)
```

```
Couldn't stat source package list ftp://ftp.nerim.net unstable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_unstable_main_binary-powerpc_Packages) - stat (2 No such file or directory)
```

```
Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-powerpc_Packages) - stat (2 No such file or directory)
```

```
Couldn't stat source package list http://ubuntu-bp.sourceforge.net warty-backports/main Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_warty-backports_main_binary-powerpc_Packages) - stat (2 No such file or directory)
```

```
Couldn't stat source package list http://ubuntu-bp.sourceforge.net warty-backports/universe Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_warty-backports_universe_binary-powerpc_Packages) - stat (2 No such file or directory)
```

Any help? Or have I screwed up the system?

---

### Post by farruinn on 2005-03-01
Could you please post your /etc/apt/sources.list?  I see a couple of things that are disturbing to me: stable and unstable is mentioned which would be a Debian specific thing, and last time I checked the marillat repository was non-PPC.  The other thing is they're all listed as source package lists so I think you must have something really funky in your sources.list.  This is what mine looks like:


# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview powerpc Binary-1 (20041020)]/ unstable main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted universe multiverse

This is a functional sources.list for Warty on PPC
-Nathan

---

### Post by godsunderstudy on 2005-03-02
My sources.list file did look like this:


```
deb http://archive.ubuntu.com/ubuntu/ warty main
#deb http://archive.ubuntu.com/ubuntu/ warty universe
#deb http://archive.ubuntu.com/ubuntu/ warty multiverse
#deb http://archive.ubuntu.com/ubuntu/ warty restricted

deb-src http://archive.ubuntu.com/ubuntu/ warty main
#deb-src http://archive.ubuntu.com/ubuntu/ warty universe
#deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ warty restricted


##############Ubuntu Security##############

deb http://security.ubuntu.com/ubuntu/ warty-security main
#deb http://security.ubuntu.com/ubuntu/ warty-security restricted
#deb http://security.ubuntu.com/ubuntu/ warty-security universe
#deb http://security.ubuntu.com/ubuntu/ warty-security multiverse

deb-src http://security.ubuntu.com/ubuntu/ warty-security main
#deb-src http://security.ubuntu.com/ubuntu/ warty-security restricted
#deb-src http://security.ubuntu.com/ubuntu/ warty-security universe
#deb-src http://security.ubuntu.com/ubuntu/ warty-security multiverse


##############Ubuntu Warty Updates################
# deb http://archive.ubuntu.com/ubuntu/ warty-updates main
# deb http://archive.ubuntu.com/ubuntu/ warty-updates restricted
# deb http://archive.ubuntu.com/ubuntu/ warty-updates universe
# deb http://archive.ubuntu.com/ubuntu/ warty-updates multiverse

# deb-src http://archive.ubuntu.com/ubuntu/ warty-updates main
# deb-src http://archive.ubuntu.com/ubuntu/ warty-updates restricted
# deb-src http://archive.ubuntu.com/ubuntu/ warty-updates universe
# deb-src http://archive.ubuntu.com/ubuntu/ warty-updates multiverse

#--------------------------------------------------------------------
#---------------------------Hoary------------------------------------
#############Ubuntu Hoary##############
# deb http://archive.ubuntu.com/ubuntu/ hoary main
# deb http://archive.ubuntu.com/ubuntu/ hoary universe
# deb http://archive.ubuntu.com/ubuntu/ hoary multiverse
# deb http://archive.ubuntu.com/ubuntu/ hoary restricted

# deb-src http://archive.ubuntu.com/ubuntu/ hoary main
# deb-src http://archive.ubuntu.com/ubuntu/ hoary universe
# deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ hoary restricted


##############Ubuntu Security##############
# deb http://security.ubuntu.com/ubuntu/ hoary-security main
# deb http://security.ubuntu.com/ubuntu/ hoary-security restricted
# deb http://security.ubuntu.com/ubuntu/ hoary-security universe
# deb http://security.ubuntu.com/ubuntu/ hoary-security multiverse

# deb-src http://security.ubuntu.com/ubuntu/ hoary-security main
# deb-src http://security.ubuntu.com/ubuntu/ hoary-security restricted
# deb-src http://security.ubuntu.com/ubuntu/ hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu/ hoary-security multiverse 
```

It now the following:
```

# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview powerpc Binary-1 (20041020)]/ unstable main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu warty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu warty main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu warty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu warty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu warty universe
# deb-src http://archive.ubuntu.com/ubuntu warty universe

deb http://security.ubuntu.com/ubuntu warty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu warty-security main restricted universe multiverse
```

i.e. Exactly the same as yours. However, now the volume of error messages has increased:


```
Couldn't stat source package list http://archive.ubuntu.com warty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)

Couldn't stat source package list http://archive.ubuntu.com warty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_universe_binary-powerpc_Packages) - stat (2 No such file or directory)

Couldn't stat source package list http://archive.ubuntu.com warty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_multiverse_binary-powerpc_Packages) - stat (2 No such file or directory)

Couldn't stat source package list http://archive.ubuntu.com warty-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty-updates_main_binary-powerpc_Packages) - stat (2 No such file or directory)

Couldn't stat source package list http://archive.ubuntu.com warty-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty-updates_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)

Couldn't stat source package list http://archive.ubuntu.com warty-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty-updates_universe_binary-powerpc_Packages) - stat (2 No such file or directory)

Couldn't stat source package list http://archive.ubuntu.com warty-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty-updates_multiverse_binary-powerpc_Packages) - stat (2 No such file or directory)

Couldn't stat source package list http://security.ubuntu.com warty-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_warty-security_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)

Couldn't stat source package list http://security.ubuntu.com warty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_warty-security_universe_binary-powerpc_Packages) - stat (2 No such file or directory)


Couldn't stat source package list http://security.ubuntu.com warty-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_warty-security_multiverse_binary-powerpc_Packages) - stat (2 No such file or directory)
```

---

### Post by farruinn on 2005-03-02
Remember that whenever you make a change to sources.list you must click the Reload button in Synaptic or run 'sudo apt-get update' from a shell....

-Nathan

---

