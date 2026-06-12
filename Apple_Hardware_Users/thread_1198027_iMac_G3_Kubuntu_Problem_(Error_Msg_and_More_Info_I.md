---
title: "iMac G3 Kubuntu Problem (Error Msg and More Info Inside)"
date: 2009-06-26
forum: Apple Hardware Users
---

### Post by WB2Colorado on 2009-06-26
Hi,
I have Kubuntu installed on my iMac G3. I'm having a bit of a problem, though. I can't install updates or new programs via the update manager or the Software manager. Here is the error message I get:

A problem that we were not expecting has occured. Please report this bug with the error description.

-details-

The backend took too much time to process the synchronous request - you need to fork!

I am a new user to Ubuntu, so what that just said went right in one ear and out the other. I don't really know what it means. I'm sure it's just a fancy way of telling me that my computer is too old to be running Kubuntu, but the strange thing is that I'm not having any problems with other programs (yet).

This computer did have Ubuntu installed on it before, but I wanted to see how it would handle Kubuntu for a while. I never had problems with Ubuntu, so this is a Kubuntu problem.

---

### Post by tiagobt on 2009-06-28
What happens if you run the following commands in a terminal window (Konsole)?

```
sudo apt-get update
sudo apt-get upgrade
```

The error message you posted seems to be a bug in KPackageKit ([bug 272410](https://bugs.launchpad.net/packagekit/+bug/272410)), but apt-get should still work. If this is the case, you could replace KPackageKit by Adept or Synaptic.

---

