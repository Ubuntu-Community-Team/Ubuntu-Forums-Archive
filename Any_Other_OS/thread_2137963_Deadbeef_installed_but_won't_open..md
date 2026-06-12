---
title: "Deadbeef installed but won't open."
date: 2013-04-22
forum: Any Other OS
---

### Post by kabukiM0n0 on 2013-04-22
Hey there. 

I installed Deadbeef, downloaded v.5.5 extracted then ./configure - make - make install 
It acts as if it was installed and the output of ```
whereis
``` ```
/usr/local/bin/deadbeef /usr/local/lib/deadbeef 
```But when I try to open it whether it be from terminal or manually. Nothing happens. I've run top while attempting to open it doesn't even appear. 

What have I done wrong? I've been having problems with gstreamer and had to install them all, but I doubt that would have anything to do with it.

---

### Post by dodo3773 on 2013-04-22
If you don't get any errors you could do a:
```

strace -e open deadbeef

```

Maybe it will give you a little more info as to what's holding it up. Also, did you build it against gtk2 or gtk3? I would try building against gtk2 and see if that helps.

---

### Post by kabukiM0n0 on 2013-04-23
I uninstalled it and tried again, make install gives out a ffmpeg.lo [error 1] - at least that is the only error I can find.
 FFmpeg is installed and Deadbeef seems to install but still doesn't respond. It seems to be a bug from what I can find against that error, maybe I'll try an older version. 

I built it on Gtk2.

---

### Post by Elastic_Potential on 2013-12-04
bump because I'm experiencing the same issue, despite installing the .deb version 0.6.0-2

In addition, I thought it would be beneficial to show a DPKG paradox in which it appears to install deadbeef; however, when I try dpkg -r, it claims that deadbeef hasn't even been installed:
```

aesclepius@Sera:~/downloads$ sudo dpkg -i deadbeef-static_0.6.0-2_i386.deb
(Reading database ... 90635 files and directories currently installed.)
Preparing to replace deadbeef-static 0.6.0-2 (using deadbeef-static_0.6.0-2_i386.deb) ...
Unpacking replacement deadbeef-static ...
Setting up deadbeef-static (0.6.0-2) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
aesclepius@Sera:~/downloads$ deadbeef
bash: deadbeef: command not found
aesclepius@Sera:~/downloads$ sudo dpkg -r deadbeef
dpkg: warning: ignoring request to remove deadbeef which isn't installed

```

---

