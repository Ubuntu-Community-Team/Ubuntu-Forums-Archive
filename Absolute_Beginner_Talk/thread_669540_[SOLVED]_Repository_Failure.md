---
title: "[SOLVED] Repository Failure"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by arvevans on 2008-01-16
In Synaptic Package Manager, I clicked on RELOAD and got an error message which seems to indicate that two repositories are inaccessible:
:
[INDENT]**Could not download all repository indexes**

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:) 302 Found[/INDENT]

Should I be concerned about this?  Is there a fix for it?

Arv
_._

---

### Post by philinux on 2008-01-16
The medibuntu repos are as found by clicking link below. Not sure what the ones you got.

You can check yours under system>Admin>software sources.

---

### Post by nikoPSK on 2008-01-16
The medibuntu repos are down. This happens to me too, hopefully back up soon. :)

---

### Post by arvevans on 2008-01-16
But I can go to:

[INDENT][http://www.medibuntu.org/](http://www.medibuntu.org/)[/INDENT]

and download & install the applications.  This would seem to indicate that there might be a problem with the repository name?  I'm not an expert in this area...obviously.

Arv
_._

---

### Post by kostkon on 2008-01-16
> **arvevans said:**
> But I can go to:

[INDENT][http://www.medibuntu.org/](http://www.medibuntu.org/)[/INDENT]

and download & install the applications.  This would seem to indicate that there might be a problem with the repository name?  I'm not an expert in this area...obviously.

Arv
_._

The *Medibuntu* people transfered the url of the repository to the *medibuntu.org* domain and stopped using the *medibuntu.sos-sts.com* one. I assume the latter is not working anymore.

Go to* System -> Administration -> Software Sources* and delete the old *Medibuntu* repository  (and any applicable key) from your sources. The go to this [Ubuntu documentation page]("https://help.ubuntu.com/community/Medibuntu")  for instructions on how to add it back.

---

### Post by arvevans on 2008-01-16
That fixed the problem.  Thank you very much.
Mark this one as CLOSED

Arv
_._

---

### Post by SOULRiDER on 2008-01-16
> **arvevans said:**
> That fixed the problem.  Thank you very much.
Mark this one as CLOSED

Arv
_._

Actually, you should mark it a solved :P [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by nikoPSK on 2008-01-16
> **kostkon said:**
> The *Medibuntu* people transfered the url of the repository to the *medibuntu.org* domain and stopped using the *medibuntu.sos-sts.com* one. I assume the latter is not working anymore.

Go to* System -> Administration -> Software Sources* and delete the old *Medibuntu* repository  (and any applicable key) from your sources. The go to this [Ubuntu documentation page]("https://help.ubuntu.com/community/Medibuntu")  for instructions on how to add it back.

thank ya!

---

