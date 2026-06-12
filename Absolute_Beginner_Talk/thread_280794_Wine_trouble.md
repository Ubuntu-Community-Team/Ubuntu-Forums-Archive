---
title: "Wine trouble"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by StormGuy on 2006-10-20
Is Wine no longer available for Ubuntu?  Whenever I try to get-apt wine, I get the following error:

---------------------------------------------
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
---------------------------------------------

I'm sure I'm doing something dumb...but I'onno what :(

---

### Post by Iarwain ben-adar on 2006-10-20
Hi,
have you enabled the right repo's?

Read about that [here]("https://help.ubuntu.com/community/Wine?highlight=%28wine%29")

Or just enable multiverse, [here]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096")


Iarwain

---

### Post by StormGuy on 2006-10-20
I tried following those instructions, but I get the following whenever I reload after making the changes:

---
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
---

---

### Post by Iarwain ben-adar on 2006-10-21
Hi,
try to get a new one from [here](http://www.psychocats.net/ubuntu/sources.php).

See how that goes :D


Iarwain

---

