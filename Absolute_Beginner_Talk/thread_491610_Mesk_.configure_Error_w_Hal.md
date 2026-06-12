---
title: "Mesk ./configure Error w/ Hal"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by makaira on 2007-07-03
This is what I get during the configure process for the current Mesk build. I've installed hal through the Synaptic Package Manager and I'm not exactly sure what to do next.

```

checking for hal... configure: error: Package requirements (hal >= 0.5.7) were not met:

No package 'hal' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables hal_CFLAGS
and hal_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by Point Ex on 2007-07-17
```
sudo apt-get install libhal-dev
```
Always try to find the dev package for the dependencies.

---

