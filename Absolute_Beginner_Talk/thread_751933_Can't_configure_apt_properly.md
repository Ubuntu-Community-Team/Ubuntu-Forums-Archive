---
title: "Can't configure apt properly"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by abhijitvalluri on 2008-04-11
Hi,
I recently installed Ubuntu 7.10 on a PC. The installation hanged at 82% (I think),  at ***configuring apt. ***It got stuck there for nearly 20 minutes. I previously installed it on another PC without such a glitch. I unplugged my network cable and it gave the error that security updates haven't been configured. I finished the installation and configured the repositories manually by synaptic and reset the repositories to a nearby ftp site. Everything worked fine except that synaptic ***still ***tries to download security updates from security.ubuntu.com. In my previous experience with Gutsy on the other machine, I haven't had such a problem. All the updates were downloaded from the ftp server that I chose in synaptic, including security updates. But now, security updates are being downloaded from security.ubuntu.com while everything else downloads from the ftp server I chose.:confused:

Please help me configure synaptic such that even security updates are downloaded from the other ftp server.

P.S. By the way, why is synaptic behaving like this, downloading from a repo that I haven't configured it to download from???:confused:

---

### Post by kesman on 2008-04-11
You could check system -> administration -> software sources for your repositories. I think that security updates are **always** downloaded from that server you mentioned. Don't they work for you or what's the problem here?

---

### Post by eternicode on 2008-04-11
> **kesman said:**
> Don't they work for you or what's the problem here?

:o maybe they have an illegal, unlicensed installation and want to avoid detection :o

:lolflag:

Have you peeked inside your /etc/apt/sources.list file?  Check to see if this repo is in there, and remove it if it is, then run "sudo apt-get update".

---

### Post by zvacet on 2008-04-11
> But now, security updates are being downloaded from security.ubuntu.com while everything else downloads from the ftp server I chose

Nothing to be worried about,or to fix.That is exactly how should be.You can look [here.](http://easylinux.info/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories)

---

### Post by abhijitvalluri on 2008-04-11
> **zvacet said:**
> Nothing to be worried about,or to fix.That is exactly how should be.You can look [here.]("http://easylinux.info/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories")

Well, I don't think that's exactly how apt is configured on my other PC. On it, I can download security updates in a flash as the ftp server it's configured to use is right within the institute I live in. Where as this new installation of Gutsy takes a lot of time to download the updates as it downloads from security.ubuntu.com and the net connection is pretty slow. In short, my old PC is configured to update from a local repo while the new one downloads from security.ubuntu.com

:( Pretty strange.
By the way, the updates do work. They are only very slow.

---

### Post by eternicode on 2008-04-11
If both comps use a variant of Ubuntu, you could just copy over the sources.list from the working comp to the new comp (be sure to rename/backup the sources.list on the new comp).  Then update apt and see if it works.

---

