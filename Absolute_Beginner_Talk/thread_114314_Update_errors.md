---
title: "Update errors"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by jasidog on 2006-01-08
Um I guess this may not be the appropriate forum but I am a beginner and felt the answers i got elsewhere may confuse me. 

When I get notification for updates and open the update manager it partially works but I also get error messages as follows - 

```
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
```

Same message pops up when i use the Synaptic Package Manager. Which I guess is the same thing.

Is this something to worry about? Is there something i should be doing?

Thanks for any help :???: :)

---

### Post by meborc on 2006-01-08
the fault is most probably in your **/etc/apt/sources.list**...

try **sudo gedit /etc/apt/sources.list** ... it will prompt you for your passeord... insert it... hit enter... gedit will lounch with the file... change the contents of the file to:```
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

then you should be OK...

do [B]
sudo apt-get update
sudo apt-get upgrade[/B]

---

### Post by jasidog on 2006-01-08
That worked perfectly! Thanks for being so helpful, it's appreciated. :)

In fact looking around these forums and seeing how people with problems were  helped out. Was one of the main reasons I tried out Ubuntu over other distros.

Thanks again! :)

---

