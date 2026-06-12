---
title: "can't connect to universe repository"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by carleton on 2006-05-22
I've been pulling my hair out trying to connect the universe repository, but everytime I try to add it in Synaptic or access it from the terminal I get an error that goes something like this:
```

**Cannot Download All Repository Indexes**

http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
```

I tried running apt-get update, but it gives me a similar error, and of course the terminal suggests I run apt-get update to fix the problem. 

Any help would be appreciated,

Cheers,

Carleton

---

### Post by meborc on 2006-05-22
try to manually edit your sources.list file... that is the file apt uses for web-locations..

but first make a backup ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

then:

```
sudo gedit /etc/apt/sources.list
```

gedit will open the file... delete all, and replace with the following

```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

```

now do 

```
sudo apt-get update
sudo apt-get upgrade
```

theoretically it should work... i'm using dapper, so i can't check... if anything goes wrong, you can always restore the original file from the backup using ```
sudo cp /etc/apt/sources.list.backup /etc/apt/sources.list
```

---

### Post by carleton on 2006-05-23
Thanks for the resopnse, but that didn't seem to help. I changed my source list as you reccomended but when i tried to update i got the following error message:

```
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com breezy-updates/main Packages
  Could not open file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists _breezy-updates_main_binary-i386_Packages - open (2 No such file or directory)
99% [18 Sources bzip2 0] [Waiting for headers]                      35.3kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com breezy-updates/main Sources
  Could not open file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists _breezy-updates_main_source_Sources - open (2 No such file or directory)
99% [19 Sources bzip2 0] [Waiting for headers]                      35.3kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com breezy-updates/restricted Sources
  Could not open file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists _breezy-updates_restricted_source_Sources - open (2 No such file or directory)
Get:20 http://archive.ubuntu.com breezy/universe Packages [3028kB]
Get:21 http://archive.ubuntu.com breezy/universe Packages [3028kB]
99% [20 Packages gzip 0]                                            35.3kB/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/universe Packages
  Sub-process gzip returned an error code (1)
99% [21 Packages gzip 0]                                            35.3kB/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 297kB in 8s (36.8kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binar y-i386/Packages.gz  Could not open file /var/lib/apt/lists/partial/archive.ubunt u.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages - open (2 No such fi le or directory)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/sourc e/Sources.gz  Could not open file /var/lib/apt/lists/partial/archive.ubuntu.com_ ubuntu_dists_breezy-updates_main_source_Sources - open (2 No such file or direct ory)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted /source/Sources.gz  Could not open file /var/lib/apt/lists/partial/archive.ubunt u.com_ubuntu_dists_breezy-updates_restricted_source_Sources - open (2 No such fi le or directory)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i3 86/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i3 86/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe P ackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe P ackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe P ackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe P ackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy/main Packages ( /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packa ges)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy/restricted Pack ages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binar y-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-updates/main Pa ckages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_b inary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-updates/restric ted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_ restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.
carleton@pca2:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
```

any other suggestions? Could this be a problem with my computer's network interface or is there something going on with the list?

Thanks,

Carl

---

### Post by Mustard on 2006-05-23
I'm wondering why its coming up with duplicate sources.list entries when you have just blanked the old sources.list and copied a completely new one in.

-edit-

Hmm..there are quite a few duplications of sources in the example sources.list given above now that I look at it closely.

I'm not sure what this bzip2 error is all about.

I'm also curious why in the above output a lot of entries have a space in the middle of them, for example see the bold text in the entry below.  What is this space doing in there?  I guess it must be some type of glitch in the copy and paste. :)

```
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe **P ackages** (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
```

I would be trying a different mirror with your sources.list to see if it is a problem with a specific mirror of the ubuntu repos.  Try going to this link below and creating a sources.list for maybe a canadian mirror of the repos and see if it gives the same errors.

[http://ubuntulinux.nl/source-o-matic](http://ubuntulinux.nl/source-o-matic)

---

### Post by catlett on 2006-05-23
[http://www.ubuntuforums.org/showthread.php?t=179683](http://www.ubuntuforums.org/showthread.php?t=179683)

---

