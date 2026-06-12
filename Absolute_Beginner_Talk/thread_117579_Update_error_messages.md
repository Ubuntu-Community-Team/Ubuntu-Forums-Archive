---
title: "Update error messages"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by utab on 2006-01-15
Hi all,

When I type sudo apt-get update I got error and warning messages concerning backports and multiuniverse.

 I got similar errors when I try to install some applications, eg. rar,

I pasted the full list somewhat long, Sorry 

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg
  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30.9kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [19.6kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [5470B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [10.4kB]
47% [11 Packages bzip2 0] [Waiting for headers]                      6167B/s 9s
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [769kB]
93% [12 Packages gzip 0] [Connecting to archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  Sub-process gzip returned an error code (1)
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages [4735B]
93% [Connecting to archive.ubuntu.com (82.211.81.182)]               6167B/s 9s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
  Sub-process gzip returned an error code (1)
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources [305kB]
95% [Working]                                                        6167B/s 9s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
  Sub-process gzip returned an error code (1)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [3028kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources [1223kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [116kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources [58.0kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [24.4kB]
20% [Connecting to archive.ubuntu.com (82.211.81.182)]              179kB/s 25s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
  Sub-process gzip returned an error code (1)
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [20B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [5467B]
20% [Connecting to archive.ubuntu.com (82.211.81.182)]              179kB/s 25s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
  Sub-process gzip returned an error code (1)
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [20B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [25.6kB]
20% [Connecting to archive.ubuntu.com (82.211.81.182)]              179kB/s 25s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
  Sub-process gzip returned an error code (1)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Fetched 44.0kB in 14s (3111B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz)  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by bags on 2006-01-15
i don't know about your error but try to use my sources.list file, maybe your is damaged...
> deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse


copy the quote in a new file called sources.list; then type
> cd /etc/apt/
sudo mv sources.list sources.list.backup
and then copy the new sources.list in /etc/apt/ with something like:
> sudo cp /whereitis/sources.list /etc/apt/
finally try to run sudo apt-get update.... :D

---

### Post by utab on 2006-01-15
thank you for the help but Still some of the files could not be retreived

Is that common or do I have to end up without errors and W messages?

thx

such as

ailed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
utab@c140:~/c++_progs$ clear

utab@c140:~/c++_progs$ openssh
bash: openssh: command not found
utab@c140:~/c++_progs$ sudo openssh
Password:
sudo: openssh: command not found
utab@c140:~/c++_progs$ sudo ssh
usage: ssh [-1246AaCfgkMNnqsTtVvXxY] [-b bind_address] [-c cipher_spec]
           [-D port] [-e escape_char] [-F configfile]
           [-i identity_file] [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [user@]hostname [command]
utab@c140:~/c++_progs$  cd /etc/apt/
utab@c140:/etc/apt$ udo mv sou
bash: udo: command not found
utab@c140:/etc/apt$ udo mv sou
bash: udo: command not found
utab@c140:/etc/apt$ sudo mv sources.list sources.list.backup
Password:
utab@c140:/etc/apt$ cp ~/sources.list /etc/apt
cp: cannot create regular file `/etc/apt/sources.list': Permission denied
utab@c140:/etc/apt$ sudo cp ~/sources.list /etc/apt
utab@c140:/etc/apt$ sudo apt-get update
Get:1 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release
Get:4 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Get:7 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release [30.9kB]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Get:8 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release [19.6kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [10.4kB]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Get:10 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Sources [232kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [25.6kB]
66% [11 Packages gzip 0] [10 Sources 113489/232kB 48%] [Connecting to archive.u
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
  Sub-process gzip returned an error code (1)
Get:12 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages [33B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1241B]
Get:14 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages [33B]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
  Error reading from server - read (104 Connection reset by peer)
Get:15 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages [33B]
Get:16 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages [33B]
Get:17 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Sources [1454B]
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Sources
Get:18 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages [2304kB]
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages
Get:19 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Packages [586kB]
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Packages
Get:20 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Packages [5061B]
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Packages
Get:21 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Packages [91.9kB]
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Packages
Get:22 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Packages [21.4kB]
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Packages
Get:23 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Packages
Get:24 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Sources [5470B]
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Sources
Get:25 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Sources
  416 Requested Range Not Satisfiable
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages
  Error reading from server - read (104 Connection reset by peer)
Get:26 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Packages [769kB]
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Packages
  Error reading from server - read (104 Connection reset by peer)
Get:27 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Packages [4735B]
8% [27 Packages gzip 0] [Connecting to it.archive.ubuntu.com (194.185.88.30)]
gzip: stdin: not in gzip format
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Packages
  Sub-process gzip returned an error code (1)
Get:28 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Packages [116kB]
11% [Working]                                          40.9kB/s 49710d 6h26m44s
gzip: stdin: not in gzip format
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Packages
  Sub-process gzip returned an error code (1)
Get:29 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Packages [24.4kB]
11% [Connecting to it.archive.ubuntu.com (194.185.88.30)]
gzip: stdin: not in gzip format
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Packages
  Sub-process gzip returned an error code (1)
Get:30 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Packages [20B]
Get:31 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Sources [5467B]
11% [Connecting to it.archive.ubuntu.com (194.185.88.30)]
gzip: stdin: not in gzip format
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Sources
  Sub-process gzip returned an error code (1)
Get:32 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Sources [20B]
Fetched 419kB in 40s (10.3kB/s)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  416 Requested Range Not Satisfiable
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

