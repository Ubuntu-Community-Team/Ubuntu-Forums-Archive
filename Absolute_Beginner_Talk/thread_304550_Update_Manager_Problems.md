---
title: "Update Manager Problems"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Kevin Funnell on 2006-11-21
I nedd help to rectifiy the following:

When trying to update packages with Update Manager or Synaptic Package Manager I receive the following Pop-Up Message

The following problems were founfd on your system:

E: Could not get lock /var/cache/apt/archives/lock - open(11 Resource temporarily unavailable)
E: Unable to lock the download directory

I first tried to update yesterday and received the above Pop-Up & received again today when trying to update.

Could I get help (point me in the right direction) or tell me how to rectify this problem.

Thanks in advance,

Old Kevin

---

### Post by ingo on 2006-11-22
Seems weird. It appears as though another programme has access to your cache. Nothing else open like aptitude or something? If so, close first and Bob's your uncle. Otherwise delete the lock file (this gets generated automatically, so no sweat):

$ sudo rm /var/cache/apt/archives/lock

And then try again.

---

### Post by Kevin Funnell on 2006-11-22
Thanks, for your fix appears to of rectified the problem, Updates worked now I am current with Mozilla Firefox & Thunderbird.

Old Kevin:D

---

