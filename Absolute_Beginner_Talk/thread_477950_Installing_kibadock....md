---
title: "Installing kibadock..."
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-06-18
As the title suggests, I'm trying to install kiba dock, using the commands at:

[http://ubuntuforums.org/showthread.php?t=26a8645](http://ubuntuforums.org/showthread.php?t=26a8645)

And after this command:

```

david@david-desktop:~/kibadock/trunk$ ./autogen.sh

```

I get (after several pages of text checking for this and that):

```

checking for GNOME_DESKTOP... configure: error: Package requirements (gnome-desktop-2.0 >= 2.8) were not met:

No package 'gnome-desktop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_DESKTOP_CFLAGS
and GNOME_DESKTOP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```


How do I fix this? I see no packaged called gnome-desktop-2.0 in synaptic...

---

### Post by Neon_Knight on 2007-06-18
It's ok, ignore this thread, I sorted it by installing libgnome-desktop-dev

And a similar libxml problem by installing libxml-dev.

---

