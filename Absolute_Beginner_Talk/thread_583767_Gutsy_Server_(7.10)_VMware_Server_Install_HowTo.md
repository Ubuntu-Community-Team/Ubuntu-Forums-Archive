---
title: "Gutsy Server (7.10) VMware Server Install HowTo"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by John.Gallogly on 2007-10-20
I ran into some problems getting VMware Server installed properly on my Gutsy Server (no gui).  Here is what worked for me:

Thanks to AdamLis over at HowToForge.com. His post at describes the prerequisites for VMware Server to install properly. His post was directed towards Debian Edgy but the packages he listed installed for me. The thread is located at [http://www.howtoforge.com/debian_etch_vmware_server_howto](http://www.howtoforge.com/debian_etch_vmware_server_howto)

In short these are the packages needed 

    * linux-headers-`uname -r`
    * libc6-dev
    * gcc
    * make
    * psmisc
    * x11-common
    * libxau6
    * libxdmcp6
    * libx11-data
    * libx11-6
    * libxrender1
    * libice6
    * libxext6
    * libxtst6
    * libsm6
    * libxt6
    * libxi6

Also make sure to do build-essential and xinetd.

After all the prerequisites are installed head over to VMware and download the latest server tarball (1.0.4 is latest) [http://vmware.com/download/server/]("http://vmware.com/download/server/")
Also download the Any-Any patch located at [http://knihovny.cvut.cz/ftp/pub/vmware/]("http://knihovny.cvut.cz/ftp/pub/vmware/") The latest is [vmware-any-any-update114.tar.gz]("http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz")

From there, follow the steps located over at [http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/]("http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/")
You can skip steps 1 and 2.

---

### Post by StreLochKi on 2007-10-22
TNX tnx TNX finally someone whit a GOOD "to the point" how to on libs :popcorn:

---

### Post by SilverWave on 2007-11-17
You don't need the patch anymore :)

[http://ubuntuforums.org/showthread.php?t=591732](http://ubuntuforums.org/showthread.php?t=591732)

---

