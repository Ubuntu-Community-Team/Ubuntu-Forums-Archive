---
title: "[SOLVED] &amp;quot; ./configure &amp;quot; problem"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by jagannath on 2007-10-24
Hi people,

Trying to install 'gwget'  from a tarball.

While doing " ./configure " getting the following message:

        configure: error: C compiler cannot create executables

What should I do??

Thanks in advance.

--
J

---

### Post by Paul820 on 2007-10-24
From the terminal:
> sudo apt-get install build-essential

---

### Post by rsambuca on 2007-10-24
In case you weren't aware, but gwget is in the ubuntu repositories, so you can easily install it using the Synaptic Package Manager, or from the terminal:```
sudo apt-get install gwget
```

---

### Post by jagannath on 2007-10-24
Thanks Paul. But I'm stuck again as you can see from the following:
-----------------------------------------------------------------------
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GNOME... configure: error: Package requirements (libgnomeui-2.0 >= 2.0.0
                          gtk+-2.0      >= 2.6.0
                          gmodule-2.0
                          libglade-2.0  >= 2.0.0
                          gnome-vfs-2.0
                          gnome-vfs-module-2.0) were not met:

No package 'libgnomeui-2.0' found
No package 'gtk+-2.0' found
No package 'gmodule-2.0' found
No package 'libglade-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_CFLAGS
and GNOME_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
------------------------------------------------------------------------------
That's right rsambuca ! It is there in the package manager. Can't see how I missed it, I'd looked for it there!!

--
J

---

### Post by mevets on 2007-10-24
you should apt-get all those packages its says it didnt find, start with libgnomeui and ending at gnome-vfs-module-2.0

Sometimes I notice those arnt the package name and apt cant install it, so it would be wise for you to use synaptic if the package names cannot be found when you run apt-get

---

### Post by jagannath on 2007-10-24
That's right rsambuca !! 
Wondering how I missed it !!:oops:

But it when installing thru Synaptic it says the software is not autheticated.
Wonder if it would be safe to go ahead. Don't want to mes up my system!!

--
J

---

### Post by rsambuca on 2007-10-24
You must have something wrong with your Repository Authentication Keys, since this program is in the standard Ubuntu Universe repository.  You should be fine installing it.

---

### Post by jagannath on 2007-10-24
Yup. Have installed it. Just trying it out. Actually all this exercise was to download Gutsy desktop version.

Thanks,

--

J

---

