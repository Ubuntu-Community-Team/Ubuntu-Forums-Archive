---
title: "updates and xine"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by caratuco on 2007-06-15
A week or so ago i had been testing feisty to see if I wanted to install it on my main system. I liked it so much I did so. For some reason I cannot "sudo apt-get install xine" which I was able to do a week ago. Also, I keep getting error code (1) us.archive.ubuntu.com/feisty/mainpackages. and another one or two repositories. Anyway, the Gstreamers packages are not showing up in the add remove programs. Does anyone know whats up?
Thanks

---

### Post by netyire on 2007-06-16
Hmm... may be some problems with the repositories. Does this help:

1. Press Alt+F2
2. Type gksu synaptic
3. Enter your password and click OK, if you are prompted to do so
4. Click Settings -> Repositories
5. Check all the boxes under "downloadable from the internet" and click close.
6. Click reload
7. Try installing again

---

### Post by caratuco on 2007-06-16
Thanks for responding netyire!
 I tried your suggestion and it was not recognized. Tried running as root, the same. I have tried today to update numerous times and either will get a "timed out" error or something else. I have tried to change the repositories to non-us with the same results. As of now I am not able to download any GStreamers, etc.,as suggested in Adamant1988's sticky "Enabling Multimedia in Feisty (How-To)" everything needed is just greyed out . Long story short I have no way  to play DVDs. I'm considering just going the long way and using Debians downloads, unless you or anyone has any other suggestions.

---

### Post by zvacet on 2007-06-17
```
cat /etc/apt/sources.list
```

post it here

---

### Post by caratuco on 2007-06-17
I posted the things I have tried in another thread (I hope that is not double posting) I should have stuck with this one. Here it is:

I have been trying to enable my player/burner to play dvds for a few days now with no success. A week or so ago I installed on another system and was able after an update to follow and install all of the needed packages outlined in Adamant1988's sticky. For some reason I cannot get any of the gstreamers or restricted extras to even show up in add remove programs, they are just greyed out. I downloaded synaptic, still no go. I have tried "sudo apt-get clean && sudo apt-get autoclean", "sudo mv /etc/apt/souces.list /etc/apt/sources.list.old" followed by "sudo touch /etc/apt/sources list", then "sudo apt-get updates", and "cp /etc/apt/sources.list.old /etc/apt/sources.list", and finally, sudo apt-get updates", all with no luck. I have tried "sudo aptitude update", "sudo aptutude upgrade", "sudo apt-get upgrade". in many combinations of the above,none seem to work. My sources list was created using "source-o-matic" and includes multiverse / universe . Also, I have tried using non us repositories with worse results. I'm not sure what has happened, as I said a week ago things went fine. Perhaps some legal issues?
Thanks in advance for your help.
__________________

Here is my sources list at present:

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse 

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

Thanks

---

### Post by zvacet on 2007-06-18
Try with this source list

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by caratuco on 2007-06-19
zvacet
I tried the sources list you linked to here are the results of the errors:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Connection timed out [IP: 91.189.88.31 80]
Fetched 1433kB in 42m13s (566B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Connection timed out [IP: 91.189.88.31 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

I updated a couple of times with the same results, gstreamers and ubuntu restricted are still greyed out. 
Thanks

---

### Post by zvacet on 2007-06-19
Try to change server in system<administration<software sources

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by caratuco on 2007-06-20
In another effort I tried source-o-matic using Costa Rica's servers and everthing updated fine. Weird how US servers are problamatic. Thanks for all your help!

---

