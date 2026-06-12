---
title: "Playing From Device in Music Player"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by moehabibi on 2008-04-16
Okay so some helpfull user redirected me to the ubuntu documintation site and gave me instructiions 
to download the plugin i need to read MP3 files because ubuntu only reads OGG or somthing filetype like that

that thing is  .... i have NOOO idea ... like ABSOLUTLY no idea what these instructions mean

can someone pplease explian to me how to do 
i installed ubuntu yesterday 
so pertend im the dumbest kid in the world and try to explian to me how to do it ... 

anyways heres the info 

"Ubuntu 7.10 (Gutsy Gibbon)

    *

      To play some mp3 files in rhythmbox you need to install the w32codecs package from the Medibuntu repository. If you are using the 64 bit version of Ubuntu you will need the w64codecs package instead.
    *

      Some gstreamer players (like Listen) require gstreamer0.10-plugins-ugly
" 

and oh ye ai have a 64 bit system

---

### Post by ad_267 on 2008-04-16
Installing the package ubuntu-restricted-extras will give you the mp3 codecs and other good stuff.

Click on Applications -> Accessories -> Terminal
Type 
```
sudo apt-get install ubuntu-restricted-extras
```
Type in your password and then everything should work.

If you want to use the graphical method:

Click on System -> Administration -> Synaptic Package Manager
Enter your password
Click Search and search for "ubuntu-restricted-extras"
Click in the box to the left of "ubuntu-restricted-extras" and select mark for installation.
Click apply

You may need to enable the multiverse and restricted repositories by clicking on Settings -> Repositories and ticking these then closing that window and clicking reload.

See here for more info:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

