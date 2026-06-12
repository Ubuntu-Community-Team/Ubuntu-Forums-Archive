---
title: "Quick Question"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by gamm01 on 2007-11-24
Hey guys i am completely new to ubuntu and i was trying to update my system to ubuntu 7.10 (Gusty Gibbon) and i get an error that says it cant find fakeroot, does anyone know how i can solve this? thanks

---

### Post by Paul820 on 2007-11-24
From the terminal
> sudo aptitude install fakeroot

---

### Post by gamm01 on 2007-11-24
ive tried that several times but continue to get this:

corey@croom:~$  sudo aptitude install fakeroot
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "fakeroot"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

---

### Post by gamm01 on 2007-11-24
i tried to look it up in synaptic package manager and in Add applications but i got nothin

Any suggestions??

---

### Post by dips_xe on 2007-11-24
that's weird that synaptic isn't seeing it, make sure all your repositories are enabled and you click "reload" in synaptic. if it still can't find it then download it directly:

[http://mirrors.kernel.org/ubuntu/pool/main/f/fakeroot/fakeroot_1.7.1ubuntu1_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/main/f/fakeroot/fakeroot_1.7.1ubuntu1_i386.deb")

---

### Post by seventhc on 2007-11-24
sudo apt-get install fakeroot

I just tried this and it works.

---

### Post by gamm01 on 2007-11-24
well now im getting a warning in synaptic when i try to reload

[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:) 302 Found
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:) 302 Found
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz:) Unable to fetch file, server said 'Failed to open file.  '
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz:) Unable to fetch file, server said 'Failed to open file.  '
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz:) Unable to fetch file, server said 'Failed to open file.  '
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz:) Unable to fetch file, server said 'Failed to open file.  '

this means nothing to me....i have no idea whats going on??

---

### Post by Taboo Mirage on 2007-11-24
...

**Edit:** It appears as though you're using the Breeze release?  I'd definitely recommend a completely fresh install of 7.10 rather than attempting to upgrade in this case, your version is now incredibly out of date.  You're getting 404 errors because those repositories are no longer online.  Download 7.10 from scratch, burn it and reinstall because the version you're at now is 5.10.  There's been several releases since then.

---

### Post by seventhc on 2007-11-24
> **gamm01 said:**
> i tried to look it up in synaptic package manager and in Add applications but i got nothin

Any suggestions??

> **gamm01 said:**
> well now im getting a warning in synaptic when i try to reload

[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:]("http://koti.mbnet.fi/%7Eots/ubuntu/breezy/Packages.gz:") 302 Found
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:]("http://koti.mbnet.fi/%7Eots/ubuntu/breezy/Sources.gz:") 302 Found
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz:) Unable to fetch file, server said 'Failed to open file.  '
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz:) Unable to fetch file, server said 'Failed to open file.  '
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz:) Unable to fetch file, server said 'Failed to open file.  '
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz:) Unable to fetch file, server said 'Failed to open file.  '

this means nothing to me....i have no idea whats going on??

was that from trying 'sudo apt-get install fakeroot' or from the download? :confused:

---

### Post by gamm01 on 2007-11-24
no that was just from trying to reload synaptic..nothing to really do with fakeroot just another problem i suppose

---

### Post by markharding557 on 2007-11-24
404 means it can't connect so try a different server in system-->administration-->software sources and choose a different download location

---

### Post by gamm01 on 2007-11-24
dude im getting errors for everything i try it seems like every time breezy is mentioned then an error follows..i would keep posting the errors i recieve but that would prob. get both annoying and confusing

---

### Post by Taboo Mirage on 2007-11-24
Please re-read my post:

> **Taboo Mirage said:**
> ...

**Edit:** It appears as though you're using the Breeze release?  I'd definitely recommend a completely fresh install of 7.10 rather than attempting to upgrade in this case, your version is now incredibly out of date.  You're getting 404 errors because those repositories are no longer online.  Download 7.10 from scratch, burn it and reinstall because the version you're at now is 5.10.  There's been several releases since then.

You are getting the errors because the version you're using is so old that those repositories do not even exist anymore!  You need to download a fresh ISO of the 7.10 release and install it from scratch.

Take care.

---

### Post by dips_xe on 2007-11-24
yeah, he's right, you're using 5.10 for some crazy reason.

download 7.10 !

[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

by the way, where'd you even find that?

---

### Post by seventhc on 2007-11-24
yeah, you can only do an upgrade from the previous version but that's it. you'll need a fresh install. I do think if you don't format it and leave the partition sizes the same with the same mount points and using the same user names your files may remain intact. This is not something I am sure of though since I've never tried it but I do remember reading something about it. And it seems logical enough, but again no guarentees, back up whats important before you try it...if thats not an issue, I'd do a clean install from scratch and wipe the drive.

---

### Post by gamm01 on 2007-11-24
now this might be a stupid question but wont i run into the same problem with fakeroot..i jsut got done downloading 7.10 but im not really sure how to get rid of the old one and install this new version

---

### Post by Taboo Mirage on 2007-11-24
1. The reason you cannot install "fakeroot" right now is because the the repositories you're attempting to access do not exist any longer because the version of Ubuntu you're running right now is ancient.  

2. You will not run into this problem when installing the new version because you do not need to use the old version that you have on your drive at all in order to install it.  You need to boot your PC from the installation CD, rather than the hard drive, and install Ubuntu 7.10 completely over the Linux partitions you have on your drive currently.

If you need help installing Ubuntu, I suggest checking out [this link](https://help.ubuntu.com/community/GraphicalInstall) which may be beneficial to you.  You may also wish to take a look at [this](https://help.ubuntu.com/community/Installation).

Of course if you have any further questions after attempting to install Ubuntu yourself while following these guides you should go ahead and ask.

Take care.

---

### Post by seventhc on 2007-11-24
unless burning iso images is different on your version this will work.
first put a blank cd into your burner, then right click on the iso image....( the one you just downloaded)  then left click on  "write to disk" once the cd is finished burning you boot from it. It's a live cd, so you will have a desktop once it's booted up. On your desktop you will see an icon that says install, click on that and your on your way.

---

