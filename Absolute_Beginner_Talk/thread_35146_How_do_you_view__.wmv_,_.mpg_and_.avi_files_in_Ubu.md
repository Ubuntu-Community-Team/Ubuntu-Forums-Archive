---
title: "How do you view  .wmv , .mpg and .avi files in Ubuntu"
date: 2005-05-17
forum: Absolute Beginner Talk
---

### Post by Linuxmyatuk on 2005-05-17
Guys and Girls,

I am new.. wondering how i would be able to view my video clips on my Ubuntu system.

---

### Post by bruizer on 2005-05-17
I like XMMS... It seems to handle these pretty well, and has a plug-in for Firefox. You can run these commands, but you may need to add a few extra repositories...

1. wget -c [http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb](http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb)
2. sudo apt-get install gstreamer0.8-plugins
3. sudo apt-get install w32codecs
4. sudo apt-get install liblame0
5. sudo dpkg -i gstreamer0.8-lame_0.8.8-0.1_i386.deb
6. gst-register-0.8
7. sudo apt-get install xmms
8. wget -c [http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb](http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb)
9. sudo dpkg -i xmms-wma_1.0.4-2_i386.deb

---

### Post by steve k on 2005-05-18
hey,
is there something i need to add to my apt-sources?
when i look for the try to apt-get the lame package and the w32codecs they cannot be found!
thanks!

---

### Post by Sam on 2005-05-18
Please read the [Ubuntu Guide](http://ubuntuguide.org/), your answers are there !

---

