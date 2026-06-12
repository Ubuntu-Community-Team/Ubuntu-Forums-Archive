---
title: "Restricted Drivers - 64bit"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-10-22
I remember when I first looked at 64bit Ubuntu (I think it was either Feisty, or one of the Gutsy builds) it didn't have a restricted driver for the nvidida cards.  Is this still the case?

---

### Post by steveneddy on 2007-10-22
Nope - the nVidia 64 bit **nvidia-glx-new** runs great on my Gutsy 64 bit lappie.

:popcorn:

---

### Post by cfaulkner on 2007-10-22
Under ther nvidia-glx-new restricted drivers i'm using, under the installed files, i'm showing some lib32 files in use:

```
/.
/usr
/usr/bin
/usr/bin/nvidia-bug-report.sh
/usr/bin/nvidia-settings
/usr/bin/nvidia-xconfig
/usr/lib
/usr/lib/xorg
/usr/lib/xorg/modules
/usr/lib/xorg/modules/drivers
/usr/lib/xorg/modules/drivers/nvidia_drv.so
/usr/lib/xorg/modules/extensions
/usr/lib/xorg/modules/libglx.so.100.14.19
/usr/lib/xorg/modules/libnvidia-wfb.so.100.14.19
/usr/lib/tls
/usr/lib/tls/libnvidia-tls.so.100.14.19
/usr/lib/nvidia
/usr/lib/nvidia/tls_test
/usr/lib/nvidia/tls_test_dso.so
/usr/lib/libXvMCNVIDIA.so.100.14.19
/usr/lib/libGL.so.100.14.19
/usr/lib/libGLcore.so.100.14.19
/usr/lib/libnvidia-cfg.so.100.14.19
/usr/lib/libnvidia-tls.so.100.14.19
/usr/sbin
/usr/sbin/nvidia-glx-config
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/nvidia-settings.1.gz
/usr/share/man/man1/nvidia-xconfig.1.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/nvidia-glx-new
/usr/share/bug
/usr/share/bug/nvidia-glx-new
/usr/share/bug/nvidia-glx-new/script
/usr/share/doc
/usr/share/doc/nvidia-glx-new
/usr/share/doc/nvidia-glx-new/README.txt.gz
/usr/share/doc/nvidia-glx-new/nvidia-settings-user-guide.txt
/usr/share/doc/nvidia-glx-new/README.Debian
/usr/share/doc/nvidia-glx-new/copyright
/usr/share/doc/nvidia-glx-new/examples
/usr/share/doc/nvidia-glx-new/examples/XF86Config.sample.gz
/usr/share/doc/nvidia-glx-new/changelog.Debian.gz
/usr/share/doc/nvidia-glx-new/NVIDIA_Changelog.gz
/usr/lib32
/usr/lib32/nvidia
/usr/lib32/libGL.so.100.14.19
/usr/lib32/libGLcore.so.100.14.19
/usr/lib32/libnvidia-cfg.so.100.14.19
/usr/lib32/libnvidia-tls.so.100.14.19
/usr/lib32/tls
/usr/lib32/tls/libnvidia-tls.so.100.14.19
/usr/lib/xorg/modules/libwfb.so
/usr/lib/xorg/modules/libglx.so
/usr/lib/tls/libnvidia-tls.so.1
/usr/lib/libXvMCNVIDIA_dynamic.so.1
/usr/lib/libXvMCNVIDIA.so.1
/usr/lib/libnvidia-tls.so.1
/usr/lib/libnvidia-cfg.so.1
/usr/lib/libGLcore.so.1
/usr/lib/libGL.so.1
/usr/lib32/tls/libnvidia-tls.so.1
/usr/lib32/libnvidia-tls.so.1
/usr/lib32/libnvidia-cfg.so.1
/usr/lib32/libGLcore.so.1
/usr/lib32/libGL.so.1
```

---

