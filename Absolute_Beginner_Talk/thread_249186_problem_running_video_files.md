---
title: "problem running video files"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by snutter on 2006-09-02
hello,

i cannot run video files with mpeg, avi and most extensions other than real player (which I have). I have tried video players such as Totem and noatun.

The error message is this:
```
 You do not have a decoder installed to handle this file. You might need to install the necessary plugins. 
```



Thanks

---

### Post by meng on 2006-09-02
Have you installed windows codecs? Check out
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by whizbaby on 2006-09-02
Get the codecs **meng** links to (except gstreamer0.10-pitfdll, might cause problems).
To make totem useable type **sudo apt-get install totem-xine libxine-extracodecs**
(libxine-extracodecs is in multiverse which you had to enable already)

---

