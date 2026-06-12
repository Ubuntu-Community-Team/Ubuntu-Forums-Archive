---
title: "Rythmbox aint working?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by asimmittal on 2007-12-28
I tried to use Rythmbox to play my mp3 files,  but it fails to import. Import error log says that decoding for MP3 ain't happening. I've checked on gstreamer plugin and have the latest versions.

I dont know what else to do?

---

### Post by stijngysemans on 2007-12-28
On a fresh installation i always first open an mp3 with totem. he asks "do you want to search for a codec" and it automatically installs the codec. Then you can use rhythmbox and the import feature.

---

### Post by dark_harmonics on 2007-12-28
You should try installing the following packages through synaptic or sudo apt-get install at a command line. 

Ubuntu-restricted-extras  
gstreamer0.10-plugins-bad 
gstreamer0.10-plugins-ugly 

For more information check out this:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by bapoumba on 2007-12-28
To get all the codecs, please install **ubuntu-restricted-extras** from the multiverse repositories.

---

