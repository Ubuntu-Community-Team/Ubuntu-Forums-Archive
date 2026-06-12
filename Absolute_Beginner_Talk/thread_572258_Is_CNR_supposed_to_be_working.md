---
title: "Is CNR supposed to be working?"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by devilears on 2007-10-10
I visited the cnr.com page today & noticed that the cnr-client for Ubuntu was available. Well, I downloaded & installed it, but it's not working. No icon was created on the desktop, however, one can find it under KDE->System->CNR. I clicked on a variety of software after logging into CNR.com, but all that happens is the CNR progress dialogue box that pops up and disappeares again after a while. No software gets installed. Any explinations anyone?

---

### Post by dptxp on 2007-10-10
Does any Ubuntu user use CNR ?

---

### Post by S3Indiana on 2007-10-10
> **devilears said:**
> I visited the cnr.com page today & noticed that the cnr-client for Ubuntu was available. Well, I downloaded & installed it, but it's not working. No icon was created on the desktop, however, one can find it under KDE->System->CNR. I clicked on a variety of software after logging into CNR.com, but all that happens is the CNR progress dialogue box that pops up and disappeares again after a while. No software gets installed. Any explinations anyone?Pls. ensure you've done the [following]("http://ubuntuforums.org/showthread.php?p=3478589#post3478589"):
[LIST=1]
[*] Update the sources to include [Additional Sources]("http://www.cnr.com/supportPages/communityDownloadPluginInstructions.seam#Ubuntu")
[*] Log out and back in after CNR is installed (to properly set the permissions - no reboot required)
[*] Associate package.cnr download with CNR (option provided after Install Now is selected)[/LIST]If the issue continues, open a Terminal, and from the command prompt enter: cnr (error messaging will be provided)...

---

### Post by adamklempner on 2007-10-10
It should be noted that CNR is currently in **alpha** testing, meaning it *might* work.

---

### Post by S3Indiana on 2007-10-10
> **adamklempner said:**
> It should be noted that CNR is currently in **alpha** testing, meaning it *might* work.For clarification: [CNR.com]("http://www.cnr.com") web site is [Alpha]("http://en.wikipedia.org/wiki/Software_release_life_cycle#Alpha") due to not being feature complete, but the CNR Client is Beta...

---

### Post by devilears on 2007-10-11
Did all that, results below:


devillj@L000021597:~$ cnr
[Debug]Creating InstallComplete
10/11 06:34:51.511|../src/lib/actions/InitAction.cpp|438|Action|lightup completed.
snapVersion = 0
Ubuntu OS found
Segmentation fault

---

### Post by devilears on 2007-10-11
Yes, ME! I use whatever makes life easiest.

---

### Post by S3Indiana on 2007-10-11
> **devilears said:**
> Did all that, results below:


devillj@L000021597:~$ cnr
[Debug]Creating InstallComplete
10/11 06:34:51.511|../src/lib/actions/InitAction.cpp|438|Action|lightup completed.
snapVersion = 0
Ubuntu OS found
Segmentation faultThere's an updated client [available]("http://packages.cnr.com/data/gratis/pool/c/cnr-client/0.1.2777/cnr-client_0.1.2777_i386.deb")...

---

### Post by devilears on 2007-10-11
cnr-client_0.1.2777_i386.deb? It is actually the same version I installed yesterday. I re-installed it, but same error, see below:

devillj@L000021597:~/downloads$ cnr
[Debug]Creating InstallComplete
10/11 09:33:21.584|../src/lib/actions/InitAction.cpp|438|Action|lightup completed.
snapVersion = 0
Ubuntu OS found
Segmentation fault

---

### Post by S3Indiana on 2007-10-11
> **devilears said:**
> cnr-client_0.1.2777_i386.deb? It is actually the same version I installed yesterday. I re-installed it, but same error, see below:

devillj@L000021597:~/downloads$ cnr
[Debug]Creating InstallComplete
10/11 09:33:21.584|../src/lib/actions/InitAction.cpp|438|Action|lightup completed.
snapVersion = 0
Ubuntu OS found
Segmentation faultThank You, investigating...

---

