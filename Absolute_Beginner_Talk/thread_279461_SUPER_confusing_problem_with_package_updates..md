---
title: "SUPER confusing problem with package updates."
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-10-18
I found an application I want to install. It's packaged as a .deb file. I attempt to install it, and it fails because of needed dependencies. Some libs I have are a certain version, but the package needs a higher version than what I have. I attempt to upgrade, and I get a similar message to this for all of the libs and other packages that need to be upgraded.

```
ffmpeg:
 Depends: libavcodeccvs51 but it is not going to be installed
 Depends: libavutilcvs49 but it is not going to be installed
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
  Depends: libsdl1.2debian (>=1.2.10-1) but 1.2.9-0.0ubuntu2 is to be installed
```

I thought it'd be simple to fix, by updating / installing those dependencies. I thought wrong. I search for the first entry in synaptic and find out it's not installed. I attempt to install it, and as soon as I click "mark for installation" I get this:

```
libavcodeccvs51:
 Depends: libavutilcvs49 but it is not going to be installed
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
  Depends: libfaac0 (>=1.25) but 1.24clean-0ubuntu4 is to be installed
  Depends: libfaad2-0 (>=2.5) but 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 is to be installed
  Depends: liblame0 (>=3.97) but 3.96.1-1 is to be installed
```

Even if I *CAN* get a packaged installed through synaptic (i.e. something totally not related), I always get a message that the packages that need to be updated (i.e. ones already installed) will not have anything done to them. This is explicitly stated, regardless of if I'd attempted to install those or not.

Help please? :-D 


( For reference, the app I'm trying to get on my system is kdenlive. I desperately need a video editor for .mpg files. )

---

### Post by Iarwain ben-adar on 2006-10-18
Hi,
have you enabled the multi and universe repo's?
Read [here]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096") how to do that :D

If that doesn't work,
let us know!


Iarwain

---

### Post by aysiu on 2006-10-18
You probably have conflicting repositories.

Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try again ```
sudo aptitude update
sudo aptitude install *packagename*
```

---

