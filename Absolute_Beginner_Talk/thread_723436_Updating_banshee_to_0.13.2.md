---
title: "Updating banshee to 0.13.2"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by TuxImpersonator on 2008-03-13
I'm trying to upgrade to banshee 0.13.2 but when I run ./configure but get

```
 checking for MONOZEROCONF... configure: error: Package requirements (mono-zeroconf >= 0.7.2) were not met:

No package 'mono-zeroconf' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONOZEROCONF_CFLAGS
and MONOZEROCONF_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details. 
 
```

I have run
```
 sudo aptitude install libglib2.0-dev libdbus-1-dev libdbus-glib-1-dev libgtk2.0-dev libgnomevfs2-dev libmusicbrainz4-dev libnautilus-burn-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libmono-dev monodoc libsqlite3-dev libavahi-core-dev libavahi1.0-cil 
```

which I thought would be pretty encompassing but obviously it's not! Anyone got any ideas?

---

### Post by Oldsoldier2003 on 2008-03-13
> **TuxImpersonator said:**
> I'm trying to upgrade to banshee 0.13.2 but when I run ./configure but get

```
 checking for MONOZEROCONF... configure: error: Package requirements (mono-zeroconf >= 0.7.2) were not met:

No package 'mono-zeroconf' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONOZEROCONF_CFLAGS
and MONOZEROCONF_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details. 
 
```

I have run
```
 sudo aptitude install libglib2.0-dev libdbus-1-dev libdbus-glib-1-dev libgtk2.0-dev libgnomevfs2-dev libmusicbrainz4-dev libnautilus-burn-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libmono-dev monodoc libsqlite3-dev libavahi-core-dev libavahi1.0-cil 
```

which I thought would be pretty encompassing but obviously it's not! Anyone got any ideas?

try:
```
sudo apt-get build-dep banshee
```

---

### Post by TuxImpersonator on 2008-03-13
nope, got all those, what is mono-zeroconf?

---

### Post by Oldsoldier2003 on 2008-03-13
> **TuxImpersonator said:**
> nope, got all those, what is mono-zeroconf?

there is a thread here: [http://ubuntuforums.org/showthread.php?t=6614](http://ubuntuforums.org/showthread.php?t=6614) that shows a similar problem. you could try compiling like this:
```

./autogen.sh --enable-mtp --disable-daap

make

sudo make install
``` 
Not sure if that helps you but it's a start.

---

