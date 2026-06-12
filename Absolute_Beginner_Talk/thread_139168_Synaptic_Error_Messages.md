---
title: "Synaptic Error Messages"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by utab on 2006-03-03
Dear all,

I always get this warning when I try to open Synaptic

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)

What is that?

Thanks

---

### Post by Perfect Storm on 2006-03-03
How's your sourcelist looks like?

---

### Post by welsh_spud on 2006-03-03
In terminal type in:

sudo apt-get update

That should try to update the list of repositories that you are connected to. If it leaves an error message, post it here.

---

### Post by utab on 2006-03-03
[QUOTE=welsh_spud]In terminal type in:

sudo apt-get update

That should try to update the list of repositories that you are connected to. If it leaves an error message, post it here.[/QUOTE]

This is the result

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30.9kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [40.8kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [12.3kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [28.5kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [4747B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4055B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
88% [16 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Sub-process gzip returned an error code (1)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [31.3kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [15.7kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
84% [Connecting to archive.ubuntu.com (82.211.81.151)]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
  Sub-process bzip2 returned an error code (2)
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
79% [Connecting to archive.ubuntu.com (82.211.81.151)]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
  Sub-process bzip2 returned an error code (2)
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [767kB]
94% [25 Packages gzip 0] [Connecting to archive.ubuntu.com (82.211.81.151)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  Sub-process gzip returned an error code (1)
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources [305kB]
96% [Working]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
  Sub-process gzip returned an error code (1)
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [3028kB]
98% [Working]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Sub-process gzip returned an error code (1)
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources [1223kB]
99% [Working]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
  Sub-process gzip returned an error code (1)
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [116kB]
99% [Connecting to archive.ubuntu.com (82.211.81.151)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  Sub-process gzip returned an error code (1)
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources [58.0kB]
99% [Working]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
  Sub-process gzip returned an error code (1)
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [20B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [19.0kB]
99% [Connecting to archive.ubuntu.com (82.211.81.151)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
  Sub-process gzip returned an error code (1)
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.4kB]
99% [Working]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
  Sub-process gzip returned an error code (1)
Fetched 249kB in 4s (52.2kB/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

And my souces list is

##deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

Thanks

---

### Post by welsh_spud on 2006-03-03
Well I've just looked through *all* that apt-get output and the only problem I can see is:-

..... breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_**[COLOR="DarkRed"]bi nar[/COLOR]**y-i386_Packages) - stat (2 No such ......

It looks like it has put a space in there for some reason. Your source list seems OK from what I have read. But, my only idea is that there is something wrong there, so we will replace it.

In terminal type

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

then replace everything in your sources.list with the following

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```

then type in

```
sudo apt-get update
```

If that doesn't fix your problem then I'm totally out of ideas :(

---

