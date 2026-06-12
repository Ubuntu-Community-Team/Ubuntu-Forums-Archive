---
title: "Help with internet radio"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Rollotamasi on 2007-01-26
I found a really great internet radio station on iTunes on my mac at work so I decided to add it to rythom box (Had never used rhythm box up until then)  I selected all the plug-ins that were listed but its still coming up with error "You do not have a decoder installed to handle this file. You might need to install the necessary plugins."  Is there a package or something that I should install?  Any help would be much appericated.

Thanks!

---

### Post by harlan on 2007-01-26
to install multimedia codecs, follow this

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

---

### Post by Rollotamasi on 2007-01-26
> **harlan said:**
> to install multimedia codecs, follow this

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

When I followed that guide I got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

---

### Post by Rollotamasi on 2007-01-27
Any other advice on this issue?

---

### Post by konst88 on 2007-01-27
Install everything except w32codecs.
Then follow this guide:
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

---

### Post by Jussi01 on 2007-01-27
Use automatix2 to install the codecs...

---

### Post by Jussi01 on 2007-01-28
Also many of the radio stations on Itunes are also found on streamtuner - you could check whether its there...

---

