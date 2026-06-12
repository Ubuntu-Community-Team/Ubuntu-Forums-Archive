---
title: "soucses list error"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by jorn on 2005-10-17
Hello There!
I changed my sources.list according to Ubuntu guide.
When I do the update the following message appears:
katalog)
W: Kunne ikke finde kildepakkelisten [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-i386_Packages) - stat (2 Ingen sådan fil e ller filkatalog)
W: Kunne ikke finde kildepakkelisten [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 Ingen sådan f il eller filkatalog)
W: Kunne ikke finde kildepakkelisten [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 Ingen sådan f il eller filkatalog)
tranlated:
W:Couldn't find source package list [http://ubuntu](http://ubuntu) -and so on-(2 no such file or directory)
What courses this problem?
Thank's in advance.
Jørn

---

### Post by Pablo_Escobar on 2005-10-17
Comment out backports in Your sources.list .
They are not operational.

---

### Post by LHZ on 2005-10-17
The sources you have listed are repositories for ubuntu 5.04 - Hoary Hedgehog. The current distribution is 5.10 - Breezy Badger (don't ask me about the names). Did you install 5.10 or 5.04?

If you have 5.10 (Breezy) installed, you can just change the word 'hoary' in the sources.list file to breezy:

> /var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-i386_Packages
becomes 

> /var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_breezy-backports_universe_binary-i386_Packagesand so forth.

If you have 5.04 (Hoary) installed you should probably remove them entirely (but I'm not sure on this).

It's best to be at bit cautious with [www.ubuntuguide.org](www.ubuntuguide.org) for the time being, since it hasn't been updated for Breezy yet. In particular, the repositories will need to be changed rom 'hoary' to 'breezy'.

---

### Post by jorn on 2005-10-17
Hi
Here is my list:#deb file:///cdrom/ hoary main restricted

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
Thank's for quick reply.
Jørn

---

### Post by Pablo_Escobar on 2005-10-17
Change :
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

To 
[B]
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
[/B]

---

### Post by jorn on 2005-10-17
I have got the 5.04 installed. I thought I had trouble with installing (finding different packages) because the two last lines in sources.list didn' work but maybe I'm wrong.
I'll download the 5.10 to try this version.
So long!
Jørn

---

