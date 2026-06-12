---
title: "I can't compile anything!"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by niglch on 2007-04-04
I'm running Edgy Eft, and I know this description may be very vague, but I keep getting strange problems when trying to compile software (from tarballs) on Ubuntu. Two particular programs I'm having trouble with are Audacity 1.3.2 and Jokosher 0.2. I know I have build-essentials installed and have all dependencies satisfied for both packages (including any dev files). However, when I go to compile using "make", it takes an extremely long time (like 10-20 min) and the terminal seems to loop the same sequences of code over and over (usually filled with warnings) before finally ending in failure. For example:

```
From Jokosher at failure:
Aborted (core dumped)
make[5]: *** [html-build.stamp] Error 134
make[5]: Leaving directory `/home/nick/Jokosher0.2checkout/gst/gstreamer/docs/gst'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/home/nick/Jokosher0.2checkout/gst/gstreamer/docs/gst'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/nick/Jokosher0.2checkout/gst/gstreamer/docs'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/nick/Jokosher0.2checkout/gst/gstreamer/docs'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nick/Jokosher0.2checkout/gst/gstreamer'
make: *** [all] Error 2
```

```
 From Audacity at failure:
Menus.cpp: In member function ‘void AudacityProject::OnPaste()’:
Menus.cpp:2455: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
Preprocessed source stored into /tmp/cckuFYR3.out file, please attach this to your bugreport.
make[1]: *** [Menus.o] Error 1
make[1]: Leaving directory `/home/nick/audacity-src-1.3.2-beta/src'
make: *** [audacity] Error 2
```

It isn't just these two programs either. Everything I've tried to compile so far (like wxGTK 2.8.3) has ended in some sort of error. Does anyone know what might be wrong?

---

### Post by boredandblogging.com on 2007-04-04
did you do ./configure?

Try out these two links and see if they help:
[http://www.cutlersoftware.com/ubuntuinstall/#installing_with_terminal](http://www.cutlersoftware.com/ubuntuinstall/#installing_with_terminal)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

