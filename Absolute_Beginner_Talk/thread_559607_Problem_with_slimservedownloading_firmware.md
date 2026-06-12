---
title: "Problem with slimserve/downloading firmware"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by johntinsley on 2007-09-25
Hey,
So all of a sudden when I use the package manager, or try to install or remove something, the process stops at this stage:

[B]Setting up slimserver (6.2.1-3) ...
Downloading firmware images.[/B]

Eventually it'll go on to say:

[B]svn: PROPFIND request failed on '/repos/slim/tags/RELEASE_6_2_1/server/Firmware'
svn: PROPFIND of '/repos/slim/tags/RELEASE_6_2_1/server/Firmware': could not connect to server ([http://svn.slimdevices.com](http://svn.slimdevices.com))
Failed to download firmware.[/B]

And the rest of the task will fail. Thus I haven't been able to install anything in weeks. I don't know when it start happening exactly, but I know it didn't used to happen before.

Can anyone suggest what's going on or how I might resolve it? Thanks

---

### Post by mysticmatrix on 2007-09-25
> **johntinsley said:**
> Hey,
So all of a sudden when I use the package manager, or try to install or remove something, the process stops at this stage:

[B]Setting up slimserver (6.2.1-3) ...
Downloading firmware images.[/B]

Eventually it'll go on to say:

[B]svn: PROPFIND request failed on '/repos/slim/tags/RELEASE_6_2_1/server/Firmware'
svn: PROPFIND of '/repos/slim/tags/RELEASE_6_2_1/server/Firmware': could not connect to server ([http://svn.slimdevices.com](http://svn.slimdevices.com))
Failed to download firmware.[/B]

And the rest of the task will fail. Thus I haven't been able to install anything in weeks. I don't know when it start happening exactly, but I know it didn't used to happen before.

Can anyone suggest what's going on or how I might resolve it? Thanks

Can you give us output of ```


cat /etc/apt/sources.list
```

---

### Post by johntinsley on 2007-09-25
Yes, so the output is:

# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


??

---

### Post by mysticmatrix on 2007-09-25
Sorry but I'm out of thoughts on this issue

---

