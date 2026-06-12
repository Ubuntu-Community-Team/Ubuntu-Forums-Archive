---
title: "Non-destructive reload of Ubuntu - is it possible?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by emarkay on 2007-01-23
In Windows if you use "Setup" you can reload the OS and leave your pre-existing files and data intact.  This option just overwrites the 'important' system files and whatever original drivers and registry values from the original disk,  while allowing any system changes (added software, hardware, customizations, etc.) to be preserved.

Apparently this is NOT available in Ubuntu.

FYI, I 'locked myself out of an install by confusing a username and now have lost access to most System/Administration features - including Users!  If it wasn't the 2 hour download of 100 megs of data and the Automatix info, I wouldn't care, but regardless, in the future, can this be implemented as a feature on the ISO image?

---

### Post by jimbren on 2007-01-23
If /home is a separate partition, you can reisntall without losing your personal files and settings, but you would still need to reinstall automatix and whatever you chose from there.

If you don't have /home on it's own partition, there's an excellent tutorial for doing so within a current installation here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Alternatively, you can do this when you're performing your initial installation.  

Having home on it's own partition makes for a pretty pain-free reinstalltion process when the time comes, or if you want to try out another distribution.

jimbo

---

### Post by igknighted on 2007-01-23
Try logging into recovery mode.  This gives you root powers (in terminal only though).  From here you can add your user to the Sudoers file (/etc/sudoers i think) or reset the password if you cannot remember it.

---

### Post by emarkay on 2007-02-01
I still think there should be someway to install and NOT overwrite (with appropriate warnings about this - and maybe an automated "apt-get update/upgrade") the /var/cache/apt data, and also, additionally the /home directories!

---

