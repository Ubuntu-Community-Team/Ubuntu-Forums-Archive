---
title: "Burning mp3's with serpentine"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-07-30
I am trying to burn mp3 files with serpentine, however, when I attempt to add an mp3 file, I get the error saying that the file type is not supported and to make sure that I have the correct gstreamer plugin to decode the file. Where can I get this decoder ?

---

### Post by pyros on 2007-07-30
The medibuntu repository contains multimedia codecs. for instructions on adding the repository, check this page:
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by noorez on 2007-07-30
What package(s) would I need exaclty ?

---

### Post by pyros on 2007-07-30
> **noorez said:**
> What package(s) would I need exaclty ?

Sorry, for mp3, they are in universe, not medibuntu. Go to System>Administration>Software Sources and check "Community Maintained Open Source Software (universe)" and then install "gstreamer0.10-fluendo-mp3".
That should do it, but while you are in there you may wish to install some of the other gstreamer plugins, like gstreamer-0.10-ffmpeg, gstreamer-0.10-fluendo-mpegdemux, and the gstreamer-0.10-plugins good bad (and if you find you need it, ugly).

---

