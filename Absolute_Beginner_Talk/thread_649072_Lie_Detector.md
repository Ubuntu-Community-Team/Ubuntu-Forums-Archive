---
title: "Lie Detector"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-12-24
I tried compiling "liarliar" which is supposed to be a lie detector (voice analyzer), but I couldn't get it to compile, so I looked for some debian files, and found none.

Is there any other lie detector applications out there ?

---

### Post by taurus on 2007-12-24
What's the error message and where did you download it?

---

### Post by Dr Small on 2007-12-24
I downloaded liarliar from their sourceforge project page, and here is the error message:

```
checking for gtkmm-2.0 gthread-2.0 gstreamer-0.6... Package gtkmm-2.0 was not found in the pkg-config search path. 
Perhaps you should add the directory containing `gtkmm-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtkmm-2.0' found 
Package gthread-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gthread-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gthread-2.0' found 
Package gstreamer-0.6 was not found in the pkg-config search path. Perhaps you should add the directory containing `gstreamer-0.6.pc' to the PKG_CONFIG_PATH environment variable No package 'gstreamer-0.6' found
configure: error: Library requirements (gtkmm-2.0 gthread-2.0 gstreamer-0.6) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```

That is the very end and error message when I run ./configure, as the INSTALL says.

Dr Small

---

### Post by Steveway on 2007-12-24
Well you need to install those dependencies.
Look in Synaptic for them, you need the ones that have a -dev attached to them.

---

### Post by Dr Small on 2007-12-24
I installed libgtkmm2.0-dev, but couldn't find the rest of the dependencies in synaptic. It couldn't find them... :|

---

