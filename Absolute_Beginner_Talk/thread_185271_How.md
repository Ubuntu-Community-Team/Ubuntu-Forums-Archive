---
title: "How?"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by thibeaz on 2006-05-31
Can anyone give me a link for the mp3 packages for Ubuntu 5.10 I tried already and can't find any and please just give me the link to download the files and not the apt link either I don't have internet on it yet. please help also could you send the links for mplayer too thank you

---

### Post by Jagot on 2006-05-31
All the packages can be and their dependencies can be found here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You can download the .deb's on another computer and transfer them to your Ubuntu machine to install manually.  Use the following link to guide you as to what packages you require:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by aysiu on 2006-05-31
If you're using Dapper, download [this file](http://archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1_i386.deb) to your desktop.

If you're using Breezy, download [this file](http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb) to your desktop.

Then, paste these two commands into the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

