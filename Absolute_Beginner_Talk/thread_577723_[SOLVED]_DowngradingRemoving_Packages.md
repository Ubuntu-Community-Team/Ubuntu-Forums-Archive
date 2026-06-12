---
title: "[SOLVED] Downgrading/Removing Packages"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by MatthewPlanchard on 2007-10-16
Okay, here's what's  happening:

I'm trying to install GTK+2.0 so that I can install Pidgin. GTK is dependent on pango, atk, and freetype. I downloaded the tar's for all of these and installed them with no problem, but when I go to ./configure GTK, I get the following error:

```
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.12.0    atk >= 1.9.0    pango >= 1.12.0    cairo >= 1.2.0) were not met:

Requested 'pango >= 1.12.0' but version of Pango is 1.8.2

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I tried downloading and installing the older version of Pango, but GTK still recognizes the installed version as 1.8.2.  I also tried using the Packet Manager, but I cannot find the Pango package. I tried to add the package with File->Add Downloaded Packages but synaptic still won't recognize the package.

Is there any way I can force the version down to 1.12 or downgrade/remove the package install? sudo apt-get remove Pango yields no results, nor does sudo apt-get remove Pango-1.8.2

Any suggestions?

---

### Post by julian67 on 2007-10-16
actually 1.12 > 1.8 so you don't want an older version but a newer one than is available in Feisty. You could download the source and compile and install but you might break other stuff that depends on particular versions. Or you could compile the newer version to be installed somewhere else such as /opt and then when you compile pidgin you point it to the pango libs in /opt. It's a lot of work to install something that is available as a deb

[http://www.debuntu.org/pidgin-2.2.0-.deb-released-for-ubuntu-feisty]("http://www.debuntu.org/pidgin-2.2.0-.deb-released-for-ubuntu-feisty")

---

### Post by fluffman86 on 2007-10-16
In gutsy, just "sudo apt-get install pidgin"

In feisty, go to [http://www.getdeb.net](http://www.getdeb.net) and download the pidgin.deb and install it.

---

### Post by MatthewPlanchard on 2007-10-16
Thanks a ton! I hadn't seen that getdeb site yet...that was about a hundred times easier than wha I was trying to do.

Thanks again!

---

