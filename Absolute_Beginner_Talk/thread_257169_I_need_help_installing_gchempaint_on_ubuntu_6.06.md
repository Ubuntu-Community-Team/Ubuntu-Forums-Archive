---
title: "I need help installing gchempaint on ubuntu 6.06"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by torbjorn_cederlov on 2006-09-14
Hi! I am currently trying to install gchempaint on my computer (ubuntu 6.06 LTS). I have tried sudo apt-get install gchempaint, but it doesn't work, so I have to install the program from source. When I run ./configure I get this error message:

checking for GCP... configure: error: Package requirements (gtk+-2.0 >= 2.6.0 libglade-2.0 >= 2.4.0 libgnomeprintui-2.2 >= 2.6.0 libbonoboui-2.0 >= 2.6.0 libgnomeui-2.0 >= 2.6.0 gnome-vfs-module-2.0 >= 2.6.0 gcu >= 0.4.7 shared-mime-info >= 0.12
) were not met:

No package 'gtk+-2.0' found
No package 'libglade-2.0' found
No package 'libgnomeprintui-2.2' found
No package 'libbonoboui-2.0' found
No package 'libgnomeui-2.0' found
No package 'gnome-vfs-module-2.0' found
No package 'gcu' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GCP_CFLAGS
and GCP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Can anyone please help me solve this problem. I really need this program, because chemdraw runs slow and buggy in wine....

---

