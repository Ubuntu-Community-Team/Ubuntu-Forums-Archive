---
title: "Can anyone translate from linuxish?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by izua2 on 2007-01-14
I'm trying to install some drivers, but this guy seems to have a different idea.

```

checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

```

What exactly am I looking for and where would i find it?

---

### Post by meng on 2007-01-14
Might help if you told us what you were trying to do, i.e. what is this error message in response to?

---

### Post by seshomaru samma on 2007-01-14
which drivers are you trying to install and how are you installing them?

---

### Post by izua2 on 2007-01-14
It's ./configure for the sound drivers.

Here are the first lines of the install instructions.
I jumped to step 3 since the other two make absolutely no sense to me.

```

1) You must have full configured source for the Linux kernel which you
   want to use for the ALSA drivers. Note that ALSA drivers are part
   of the kernel, so there is necessary to resolve all symbol dependencies
   between the used kernel and ALSA driver code. Partly installed kernels
   (for example from distributor makers) can be unuseable for this action.

2) You must turn on sound support (soundcore module).

3) Run './configure' script.

```

---

### Post by hal10000 on 2007-01-14
What exactly are you trying to do?
Do you want to get your sound card enabled? (Then this is the usually wrong way)

Or do you want to compile the alsa sources (this is what you're seeming to do, but then you have to install the kernel sources and i guess some other packages)

---

### Post by riven0 on 2007-01-14
If your trying to install alsa, I think all you have to do is:

> sudo apt-get install alsa

What kind of soundcard do you have, anyway?

---

### Post by 3rdalbum on 2007-01-14
Step 1:
```
sudo apt-get install linux-source
```

Step 2 I think will have already been done by Ubuntu.

Now try Step 3 again.

---

