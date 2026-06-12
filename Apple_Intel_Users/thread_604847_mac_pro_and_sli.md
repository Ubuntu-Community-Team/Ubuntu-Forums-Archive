---
title: "mac pro and sli?"
date: 2007-11-06
forum: Apple Intel Users
---

### Post by mbradlcu on 2007-11-06
Hi all,
is it possible to get both [GeForce 7300 GT] (rev a1) setup to run in sli on a mac-pro? I notice under the nvidia settings both cards are recognized but there's no sli enable option. I'm running 
NVIDIA Driver Version: 100.14.19
I've had a pretty rough time trying to upgrade to the compiled nvidia drivers btw.
thanks in advance!

---

### Post by cyberdork33 on 2007-11-06
You can use the command:
```
nvidia-xconfig --sli=on
```
to enable the SLI option in your xorg.conf

Other nVidia Driver Options:
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-d.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-d.html)

---

### Post by mbradlcu on 2007-11-06
thanks for the reply!
I should have mentioned that option was already set in my xorg.conf but still no option available using nvidia-settings proggy. any other suggestions?

thanks

---

