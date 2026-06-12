---
title: "Completely new at this and have a problem"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by dfiant on 2005-10-14
Hi... i am COMPLETELY new at this and am having a problem  puting in the codes found here:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

I try to add repositories and I get these 3 messages:

1st message:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.193 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.193 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.193 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.193 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:) 404 Not Found [IP: 82.211.81.193 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:) 404 Not Found [IP: 82.211.81.193 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:) 404 Not Found [IP: 82.211.81.193 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:) 404 Not Found [IP: 82.211.81.193 80]


2nd Message:

The following problems were found on your system:

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907


3rd message:
The following problems were found on your system:

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

Any help would be appreciated (yes... i am a noob at this.)

---

### Post by dbott67 on 2005-10-14
Try changing the repositories from **us.archive.ubuntu.com** to just **archive.ubuntu.com** (i.e. remove the '**us.**' from the address).  Then reload the packages.

-Dave

---

### Post by dfiant on 2005-10-14
didn't seem to do anything... i dunno... maybe i'm doing it wrong

---

### Post by dbott67 on 2005-10-14
Can you post your sources.list file for me please:

Enter the command **cat /etc/apt/sources.list** at a command prompt and you will get something similar to the following:
```
dbott@breezy:~$ cat /etc/apt/sources.list

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
 deb http://ca.archive.ubuntu.com/ubuntu breezy main restricted
 deb-src http://ca.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://ca.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://ca.archive.ubuntu.com/ubuntu breezy universe

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe


```

Notice that my repositories are preceded by a 'ca' because I'm in Canada; yours would say 'us' if you live in the states, etc.

If you want to edit the file, just type:
```
sudo gedit /etc/apt/sources.list /etc/apt/sources.list.bak
``` to make a backup copy, and then:
```
sudo gedit /etc/apt/sources.list
```
to make the changes as above.

-Dave

---

### Post by poofyhairguy on 2005-10-14
[QUOTE=dbott67]Can you post your sources.list file for me please:

Enter the command **cat /etc/apt/sources.list** at a command prompt and you will get something similar to the following:
```
dbott@breezy:~$ cat /etc/apt/sources.list

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
 deb http://ca.archive.ubuntu.com/ubuntu breezy main restricted
 deb-src http://ca.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://ca.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://ca.archive.ubuntu.com/ubuntu breezy universe

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe


```

Notice that my repositories are preceded by a 'ca' because I'm in Canada; yours would say 'us' if you live in the states, etc.

If you want to edit the file, just type:
```
sudo gedit /etc/apt/sources.list /etc/apt/sources.list.bak
``` to make a backup copy, and then:
```
sudo gedit /etc/apt/sources.list
```
to make the changes as above.

-Dave[/QUOTE]


Just wanted you to know that I edited the line:

 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main


Out of your sources.list. Leaving that line in can really mess up your Ubuntu system- it was not meant for Ubuntu. I suggest you remove it yourself or your next upgrade update might bring breakage!

---

### Post by dfiant on 2005-10-14
did what you said... now it just shows the same messages... only without the "us." in the line... heh

---

### Post by dbott67 on 2005-10-14
This is the "official" sources.list file.  Yours should look like it:

```
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
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

If it still doesn't work, post your sources.list here.

-Dave

---

### Post by dbott67 on 2005-10-14
[QUOTE=poofyhairguy]Just wanted you to know that I edited the line:

 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main


Out of your sources.list. Leaving that line in can really mess up your Ubuntu system- it was not meant for Ubuntu. I suggest you remove it yourself or your next upgrade update might bring breakage![/QUOTE]

Thanks... good idea.  I'm sure there would be about 7000 posts tomorrow about hosed systems thanks to some doofus from Canada! :)

-Dave

---

### Post by dfiant on 2005-10-14
thank you very much... everything works perfectly now... oh... and by the way... i'm never going back to windows again!

---

### Post by dbott67 on 2005-10-14
You're welcome.  Glad it's working now.

-Dave

---

