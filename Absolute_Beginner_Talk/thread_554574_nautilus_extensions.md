---
title: "nautilus extensions"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by MrGreen on 2007-09-19
Hi,

I am trying to get nautilus-extensions installed ... wondering if anyone has got it working out there more interested in the bluetooth stuff 

when compling get path error cannot find libnautilus-extensions

TIA

MrG

---

### Post by quixotic-cynic on 2007-09-19
Is the package you want the same as *libnautilus-extension1* which is in the repos?

For help with the compile a bit more info would be needed - the directory you where in followed by the commands typed. You might just need to use ./libnautilus-extensions instead.

Edit: I just read over the two posts below and looked around for ideas. I'm afraid that with the detail provided and my level of experience I can't help further on this one - I can't work it out. :(

---

### Post by MrGreen on 2007-09-19
thanks for that

I managed to add command via right create custom command.... [actions]

Will post error ... I have a feeling its a env path thing that needs setting up

thanks again

MrG

---

### Post by MrGreen on 2007-09-19
```
checking for NAUTILUS_ACTIONS... configure: error: Package requirements (       glib-2.0 >= 2.4.0                        gthread-2.0 >= 2.4.0                   gmodule-2.0 >= 2.4.0                     gtk+-2.0    >= 2.4.0                   libglade-2.0 >= 2.4.0                    libgnome-2.0 >= 2.7.0           libgnomeui-2.0 >= 2.7.0                 gconf-2.0 >= 2.8.0      libnautilus-extension >= 2.8.0          uuid) were not met:

No package 'libnautilus-extension' found
No package 'uuid' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables NAUTILUS_ACTIONS_CFLAGS
and NAUTILUS_ACTIONS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

---

