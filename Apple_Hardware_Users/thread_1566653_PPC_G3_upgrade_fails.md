---
title: "PPC G3 upgrade fails"
date: 2010-09-02
forum: Apple Hardware Users
---

### Post by screwballl on 2010-09-02
I have a G3 Mac using the 6.06 PPC version of Ubuntu. The Update Manager stated there is the update to PPC 8.04 LTS so I went ahead and updated it. After 6 hours of downloading and updating, now it only boots to a blank/black screen as if it is trying to use a non-native resolution.
One time I did hear the login (drum) sound but still nothing on the screen. Any way I can boot into a cli to troubleshoot this? During the entire booting process I only see black screens, a few text screens (yaboot, then another with Loading Please wait), one has the typing cursor at the top left for about 1 minute. I can hear the hard drive running and searching as if all is working and loading, just nothing on the screen.

I tried the same thing a few months ago and the only way to get it working was to put in the 6.06 alt PPC CD and format/reinstall.

Any help would be appreciated.

---

### Post by screwballl on 2010-09-02
I downloaded and installed the 8.04.1-powerpc version, it went through most of the install process and failed a few things. At the end I just had the cli with the 2.6.24-19-powerpc kernel but any attempts to load any graphical interface failed.... so now I am going back to 6.06 which at least works.

---

### Post by linuxopjemac on 2010-09-03
you need a working xorg.conf file.

---

