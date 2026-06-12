---
title: "Jahshaka"
date: 2005-05-30
forum: Art &amp; Design
---

### Post by tikal26 on 2005-05-30
I am wondering if any of you have tried Jahshaka. I want to try it, but i don't see any Debian packages. i have look for any review but i can't find any real good ones. They are sponsor by Nvidia and other good companies so i am wondering if anyone tried it allready.

---

### Post by TravisNewman on 2005-05-31
That looks slick!! I'm going to give it a shot sometime soon. The binaries are on the site, so it doesn't look like you have to do any compiling.

---

### Post by mxreader on 2005-06-01
I've been trying to install this but failed. I'm new to linux, I've followed the instructions to install all the dependencies and more... .  There is a set of instructions for debian here: 
[http://www.jahshaka.org/jahguide/index.php/CompilingOnDebian](http://www.jahshaka.org/jahguide/index.php/CompilingOnDebian)
but I got heaps of errors and it doesnt work. Here's some comment of my initial attempt:
[http://www.jahshaka.org/modules.php?name=Forums&file=viewtopic&t=359](http://www.jahshaka.org/modules.php?name=Forums&file=viewtopic&t=359)

Hope somebody else more cluey with ubuntu can help make it a nice package that can be installed with synaptic.

Ubuntu is such a nice concept/distro and great community that I think it will eventually dominate the other distros because it is easy to go from windows to Ubuntu and synaptic and the all the people that helps build those repositories certainly contributes to protecting us (not so knowlegeable) from having to climb steep learning curves and just get on with the work we love or have to do... to be productive straight away.  Meantime it looks like I have to wait until somebody more cluey helps out and make Jahshaka work with Ubuntu.

---

### Post by tikal26 on 2005-06-01
[QUOTE=mxreader]I've been trying to install this but failed. I'm new to linux, I've followed the instructions to install all the dependencies and more... .  There is a set of instructions for debian here: 
[http://www.jahshaka.org/jahguide/index.php/CompilingOnDebian](http://www.jahshaka.org/jahguide/index.php/CompilingOnDebian)
but I got heaps of errors and it doesnt work. Here's some comment of my initial attempt:
[http://www.jahshaka.org/modules.php?name=Forums&file=viewtopic&t=359](http://www.jahshaka.org/modules.php?name=Forums&file=viewtopic&t=359)

Hope somebody else more cluey with ubuntu can help make it a nice package that can be installed with synaptic.

Ubuntu is such a nice concept/distro and great community that I think it will eventually dominate the other distros because it is easy to go from windows to Ubuntu and synaptic and the all the people that helps build those repositories certainly contributes to protecting us (not so knowlegeable) from having to climb steep learning curves and just get on with the work we love or have to do... to be productive straight away.  Meantime it looks like I have to wait until somebody more cluey helps out and make Jahshaka work with Ubuntu.[/QUOTE]
 I have the same problem, if you search in their forums apparently there is some other hoary users habing the same problems. The project sounds really good but as it is right now it is very basic, I am still working at trying to solve my proble and you can probably get some hlp in their forums.

---

### Post by rajsarkar on 2005-09-21
I also tried to install Jahshaka. 

First I transformed rpm files into deb files. then tried to install using dpkg. But could not procedd due to dependency problem. 

-Raj

---

### Post by tikal26 on 2005-09-24
There is a solution on their site some guy figured it out and post it.

---

### Post by tbfr on 2005-10-16
These packages work for me in Breezy
[http://www.mediainlinux.org/index.php/mediainlinux/downloads/multimedia_debian_packages/jahshaka_debian_package](http://www.mediainlinux.org/index.php/mediainlinux/downloads/multimedia_debian_packages/jahshaka_debian_package)

Make sure libqt3-mt is installed and install the packages using
```

dpkg -i mlt_0.2.0-1_i386.deb
dpkg -i mlt++_0.2.0-1_i386.deb
dpkg -i --ignore-depends=libqt3c102-mt jahshaka_0.2.0rc1-1_i386.deb

```

---

### Post by pixelnate on 2005-10-18
tbfr, I followed your instructions, and now every time I run synaptic, it wants to remove it because it sees it as a broken package. Any thoughts?

---

### Post by tbfr on 2005-10-21
> tbfr, I followed your instructions, and now every time I run synaptic, it wants to remove it because it sees it as a broken package. Any thoughts?

sorry, didnt see your post. quick hack to fix this yourself: 

1. double click the file jahshaka_0.2.0rc1-1_i386.deb, it should open in file roller
2. drag the file control.tar.gz to the desktop
3. double click the file control.tar.gz, should also open in file roller
4. drag the file called control to the desktop
5. edit the file with an editor like gedit and remove the dependency libqt3c102-mt
6. drag the file control back into the control.tar.gz fileroller window
7. drag control.tar.gz back into the jahshaka fileroller window. 

now remove the old package and install the edited one, eg. apt-get remove jahshaka and dpkg -i jahshaka_0.2.0rc1-1_i386.deb


ps: you could also just use this package if you trust me: [http://www.tbfr.org/jahshaka_0.2.0rc1-1_i386.deb](http://www.tbfr.org/jahshaka_0.2.0rc1-1_i386.deb)

---

### Post by reuben on 2005-11-13
I got this working. I already have libqt3-mt installed, but it was complaining about a missing dependency...so I did:

sudo dpkg -i --force-depends jahshaka_0.2.0rc1-1_i386.deb

---

### Post by motin on 2007-08-30
This program needs packaging, see bug report here [https://bugs.launchpad.net/ubuntu/+bug/133848](https://bugs.launchpad.net/ubuntu/+bug/133848)

---

