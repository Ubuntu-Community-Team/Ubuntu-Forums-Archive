---
title: "unmet dependencies"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Rij on 2007-08-19
Greetings this Sunday morning. Hopefully someone will be around to answer my question.

I am trying to install a software with "apt-get install modelnet", and I get the following error:
------------------------------------------------------------------------------------
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  modelnet: Depends: libxerces23 but it is not installable
            Depends: gexec but it is not going to be installed
E: Broken packages
-----------------------------------------------------------------------------------

1) for the 1st library, does it mean that modelnet depends on libxerces23 to be installed but the latter is not installable? (I did check that libxerces23 is indeed not installable). Does that mean that the dependencies in modelnet were generated correctly? How do I fix this? Do I have to put libxerces23 in some special folder? Sorry if all of this sounds very "novice-ey".

2) I built gexecd from the source tarball. What's wrong with it?

Thanks for your help.

---

### Post by kidcharles on 2007-08-19
The latest version of libxerces on the repositories looks like libxerces27. It's strange that the name of the package contains the version number (27) which might be your problem, since the modelnet package is looking for libxerces23. I'd say that you might try installing modelnet from source after installing the libxerces27 package in synaptic. Typically when installing from source, during the ./configure stage it will look for dependencies and be satisfied with later versions. Hopefully it will also detect the gexec you compiled/installed during that stage as well.

---

### Post by Hobo Joe on 2007-08-19
This may or may not help, but it's ALWAYS better to use the word 'aptitude' instead of 'apt-get',  particularlly with things like this, as aptitude handles dependencies bettr.

---

### Post by beejournal on 2007-08-20
Hi all.  i am running feisty desktop.
having problems with package dependencies.   attempted to install bittorrent client for linux.  i would rather be using deluge.   Add remove programs" crashes too.

how can i fix?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  bittorrent: Depends: python-wxgtk2.6 but it is not installed
              Depends: python-twisted (>= 2.0) but it is not installed
              Depends: python-crypto (>= 2.0) but it is not installed
              Depends: python-psyco but it is not installed
              Depends: python-zopeinterface but it is not installed
  deluge-torrent: Depends: libboost-date-time1.33.1 but it is not installed
                  Depends: libboost-filesystem1.33.1 but it is not installed
                  Depends: libboost-thread1.33.1 but it is not installed
  gcc: Depends: cpp (>= 4:4.1.2-3) but 4:4.1.2-1ubuntu1 is installed
       Depends: gcc-4.1 (>= 4.1.2-1) but 4.1.2-0ubuntu4 is installed
  libc6-dev: Depends: libc6 (= 2.6.1-1) but 2.5-0ubuntu14 is installed
             Depends: linux-libc-dev but it is not installed
  libstdc++6-4.2-dev: Depends: gcc-4.2-base (= 4.2.1-4) but it is not installable
                      Depends: g++-4.2 (= 4.2.1-4) but it is not installable
                      Depends: libstdc++6 (>= 4.2.1-4) but 4.1.2-0ubuntu4 is installed
E: Unmet dependencies. Try using -f.


tx in advance

---

### Post by Hobo Joe on 2007-08-20
> **beejournal said:**
> Hi all.  i am running feisty desktop.
having problems with package dependencies.   attempted to install bittorrent client for linux.  i would rather be using deluge.   Add remove programs" crashes too.

how can i fix?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  bittorrent: Depends: python-wxgtk2.6 but it is not installed
              Depends: python-twisted (>= 2.0) but it is not installed
              Depends: python-crypto (>= 2.0) but it is not installed
              Depends: python-psyco but it is not installed
              Depends: python-zopeinterface but it is not installed
  deluge-torrent: Depends: libboost-date-time1.33.1 but it is not installed
                  Depends: libboost-filesystem1.33.1 but it is not installed
                  Depends: libboost-thread1.33.1 but it is not installed
  gcc: Depends: cpp (>= 4:4.1.2-3) but 4:4.1.2-1ubuntu1 is installed
       Depends: gcc-4.1 (>= 4.1.2-1) but 4.1.2-0ubuntu4 is installed
  libc6-dev: Depends: libc6 (= 2.6.1-1) but 2.5-0ubuntu14 is installed
             Depends: linux-libc-dev but it is not installed
  libstdc++6-4.2-dev: Depends: gcc-4.2-base (= 4.2.1-4) but it is not installable
                      Depends: g++-4.2 (= 4.2.1-4) but it is not installable
                      Depends: libstdc++6 (>= 4.2.1-4) but 4.1.2-0ubuntu4 is installed
E: Unmet dependencies. Try using -f.


tx in advance

I'll say it again, aptitude is better when you get dependency problems. Actually, it's always better.

---

### Post by beejournal on 2007-08-21
actually this is a dualboot pc w/ xp
i installed nvidia drivers on xp side previously...
opening system menu -> desktop efx  forced
the clean up job and installed nvidia libs via update mgr.

deluge is missing from menu - synaptic gives warning and does
not install 

should i just reinstall .deb ?
tx.

---

