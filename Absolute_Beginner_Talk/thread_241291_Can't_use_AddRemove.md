---
title: "Can't use Add/Remove"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Jenova_Project on 2006-08-22
Hi.

I am kind of stuck :/. Firefox is able to connect to the internet and browse with no difficulties, and I am able to ping any sites. However, whenever I use any other program (such as add/remove), I am unable to access anything external (so I can't update it). I have tried using firefox to go to the location of one of the repositorys ([http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)), and that works. Gaim and ssh don't work either.

I am connecting to the internet through a wireless network (router is D-LINK DI-524, card is DWL-G630).

Please help.
Thanks.

---

### Post by Major_Stitch on 2006-08-22
Hi there!

Is there any error? Does it say something?

---

### Post by Jenova_Project on 2006-08-22
Yes. After trying to update for a while, add/remove comes up with

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems...

[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)
[http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)
[http://packages.freecontrib.org/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg)

---

### Post by Major_Stitch on 2006-08-22
Hmmm...
Go to the synaptic, then to its repositories and delete all of the repositories. Than add from each type of repositorie (update,security -||-, etc.) and type (official,universe...), and after that try to reload the package list in synaptic.
Hope it helps

---

### Post by Jenova_Project on 2006-08-22
Sorry, how do I do that? (I'm very new to ubuntu)

---

### Post by Major_Stitch on 2006-08-22
No problem, we were all new :D 

On the top panel select System->Managment->Synaptic Package Manager
Then on one of the top menus (Settings) has an option Repositories and just do what I told you in the last post. After it has been done in synaptic there is a reloda button. Hit it!

Just post again if you need help!

---

### Post by Jenova_Project on 2006-08-22
Tried what you said, and got the same error:

[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

---

### Post by Major_Stitch on 2006-08-22
Sorry to hear that...I really don't have any more ideas. Hope someone else can help. Really sorry!

---

### Post by Jenova_Project on 2006-08-22
Thanks. I appreciate it :)

---

