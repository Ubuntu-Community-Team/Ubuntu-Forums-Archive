---
title: "Conflicts between universe and backports"
date: 2005-08-25
forum: Bug Reports / Support
---

### Post by PhilippWollermann on 2005-08-25
Hi!

I've just did a complete reinstall of my Kubuntu 5.04. Directly after the first boot I copied my old sources.list (see attachment) and did an 

aptitude update && aptitude -f -r dist-upgrade.

Everything worked correctly, it upgraded nearly 280 packages.. :D But two packages were held back: amarok-arts and smbclient.

apt-get install smbclient gives:

The following packages have unmet dependencies:
  smbclient: Depends: samba-common (= 3.0.14a-3ubuntu3~5.04ubp1) but 3.0.10-1ubuntu3 is to be installed
E: Broken packages

apt-get install amarok-arts gives:

The following packages have unmet dependencies:
  amarok-arts: Depends: amarok (= 2:1.2.4-0ubuntu1~5.04ubp2) but it is not going to be installed
E: Broken packages

I removed both, because I do not need them right now. I then wanted to install gcc-4.0 and g++-4.0.. similar problems:

The following packages have unmet dependencies:
  g++-4.0: Depends: libstdc++6-4.0-dev (>= 4.0.0-7ubuntu6~5.04ubp1) but it is not going to be installed
E: Broken packages

apt-get install libstdc++6-4.0-dev g++-4.0 gives:

The following packages have unmet dependencies:
  g++-4.0: Depends: libstdc++6-4.0-dev (>= 4.0.0-7ubuntu6~5.04ubp1) but 4.0-0pre6ubuntu7 is to be installed
E: Broken packages


This is bad. :) It seems that somehow some packages got updated in universe (universe has this strange libstdc++-6-4.0-dev with version "4.0-0pre6ubuntu7") and are now preferred, eventhough the backports are newer.

Please help me.. :/

Philipp

---

### Post by André on 2005-08-25
Same thing here. Plus the smbclient package seems to have similar problems:

smbclient:
  Hängt ab: samba-common (=3.0.14a-3ubuntu3~5.04ubp1) aber 3.0.10-1ubuntu3 wird installiert


Greetings and thanks in advance for any help.

André

---

### Post by PhilippWollermann on 2005-08-25
Hi,

I've switched from caliu to mirrormax mirror now, but it didn't get better. Further I noticed, that I can't even install mozilla-firefox.. "depends on 'firefox' but is not installable".

I guess I shouldn't have reinstalled my system.. :(

Philipp

---

### Post by sbassett on 2005-08-25
Yes, it appears at this time, all of the extras packages are being ignored by apt. Has anyone tried d/ling the debs of extras and creating a local repo at stated [here](http://ubuntuforums.org/showthread.php?t=42862) ? Very interested to see if this works.

---

### Post by c0rderr0y on 2005-08-25
i am in the same boat as all of you good thing its not something i did wrong on this new install.  Please someone fix it, I want my lovely ubuntu back  ](*,)

---

### Post by acascianelli on 2005-08-25
Same here, a bunch a packages are showing up as installed locally or obsolete and it really REALLY bugs me.

---

### Post by c0rderr0y on 2005-08-25
this is a great os but it stinks  running into problems like this... they should include the backports on a dvd version or somthing... that way you have to denpend on the internet soo much for an install

---

### Post by PhilippWollermann on 2005-08-25
Well, I wouldn't even mind to install completely using the internet, but it would be much easier if the package mirrors weren't broken.. :-(

Pleeaaase fix it.. Ubuntu is such a great distribution and we would really appreciate it. O:)

---

### Post by pitarda on 2005-08-25
Well,.. I had the same problem,... but I managed to solve it.
 :razz: 

nano /etc/apt/sources.list

fix the lines:

#backports repository
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted

save source.list

then:
apt-get autoclean
apt-get update
apt-get dist-upgrade
apt-get install smbfs (to get smbmount option )

 :) 
Hope it works for you too.

---

### Post by c0rderr0y on 2005-08-25
hmm i wonder anyone try this? I would rather have the backports be fixed... than make up a fix  :???:

---

