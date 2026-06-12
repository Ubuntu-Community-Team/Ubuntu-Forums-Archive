---
title: "Trying to UPDATE"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-02-21
Hi
 I trying to update.

I have gone into Synaptic Package Manager and added multiverse where necessary.
also copied a new sources.list file with the appropriate # removed.

When I try to update I get the following:
```

[B]kent@GPS-2:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory[/B]
```

Please how do I get rid of the error and  then update?

Thanks
kent

---

### Post by s6dalane on 2006-02-21
You have to close Synaptic, when upgrading via command line.

---

### Post by kent41 on 2006-02-21
[QUOTE=s6dalane]You have to close Synaptic, when upgrading via command line.[/QUOTE]
I don't understand what you mean close.

---

### Post by Coelocanth on 2006-02-21
Did you open Synaptic Package Manager through System > Administration > Synaptic and then open a terminal as well and try updating? If so, you need to close Synaptic first if you're updating with the terminal. You can't update with them both open at the same time. That's what I think he means.

---

### Post by kent41 on 2006-02-21
[QUOTE=Coelocanth]Did you open Synaptic Package Manager through System > Administration > Synaptic and then open a terminal as well and try updating? If so, you need to close Synaptic first if you're updating with the terminal. You can't update with them both open at the same time. That's what I think he means.[/QUOTE]


That make sense but what do I do now?

---

### Post by s6dalane on 2006-02-21
Yes, exactly that. That's the only problem you have ;).

Just close it.

---

### Post by kent41 on 2006-02-21
[QUOTE=s6dalane]Yes, exactly that. That's the only problem you have ;).

Just close it.[/QUOTE]

It is closed and when try run  Synaptic I get this error
```

W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

```

What I want to do is upgrade from Ubuntu 386 to 686

---

### Post by BitTorrentBuddha on 2006-02-21
Those are repositories that they couldn't reach, they could either be down or just not working, but given the sheer number of them I would say it's not that... Perhaps something is wrong in your sources.list

---

### Post by kent41 on 2006-02-21
This is my source list

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
kent@GPS-2:~$
kent@GPS-2:~$


```

---

### Post by kent41 on 2006-02-21
Maybe a better question is how do I update to i686

---

### Post by Minyaliel on 2006-02-21
Have you tried sudo apt-get update? You can find a complete source list at psychocats.net.

---

### Post by kent41 on 2006-02-21
[QUOTE=Minyaliel]Have you tried sudo apt-get update? You can find a complete source list at psychocats.net.[/QUOTE]
Yes I have tried that.
I think the answer to the problem lies in my first post, something is locked.

---

### Post by carlosqueso on 2006-02-21
try clicking the "reload" or "refresh" button in synaptic.  It may solve your problem (it seems to a lot).  Then you should find something about a kernel-i686 package and you should install that.

---

