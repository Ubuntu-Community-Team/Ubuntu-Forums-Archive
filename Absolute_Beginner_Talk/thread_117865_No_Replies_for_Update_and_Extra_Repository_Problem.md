---
title: "No Replies for Update and Extra Repository Problem"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by utab on 2006-01-15
Hi there;

I am asking again and again the same question

I am getting error and warning messages when I try to update,  add extra repositories and install applications(I have edited sources.list before and now I do not have the original copy, I pasted a problematic list of outcome of the update process as an example; the same problem about the backports and multiuniverse persists in the addition of extra repositories.)

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
47% [11 Packages bzip2 0] [Waiting for headers] 6167B/s 9s
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
93% [Connecting to archive.ubuntu.com (82.211.81.182)] 6167B/s 9s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Sub-process gzip returned an error code (1)
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources [305kB]
95% [Working] 6167B/s 9s
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
20% [Connecting to archive.ubuntu.com (82.211.81.182)] 179kB/s 25s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Sub-process gzip returned an error code (1)
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [20B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [5467B]
20% [Connecting to archive.ubuntu.com (82.211.81.182)] 179kB/s 25s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Sub-process gzip returned an error code (1)
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [20B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [25.6kB]
20% [Connecting to archive.ubuntu.com (82.211.81.182)] 179kB/s 25s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Sub-process gzip returned an error code (1)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Fetched 44.0kB in 14s (3111B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ts/Release.gpg](http://archive.ubuntu.com/ubuntu/dis...ts/Release.gpg) Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by patrick295767 on 2006-01-15
My breezy list: 
I hope it'll help u a bit:
```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## breezy-extras
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secundairy repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secundairy are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./

deb http://www.kadu.net/download/binary/ubuntu/repo breezy main


```

---

### Post by pellgarlic on 2006-06-09
i have suggested to a couple of people already to try changing "http://" to "ftp://" in their sources.list to see if that helps.
(credit to xurizaemon: [http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error](http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error))

if not, look at my post here: [http://ubuntuforums.org/showthread.php?p=1115981#post1115981](http://ubuntuforums.org/showthread.php?p=1115981#post1115981) to see if that helps any.

---

