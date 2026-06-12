---
title: "Missing package when tyring to compile stepmania"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Sir_Sid on 2007-11-04
Hi, I am missing something when I try to compile stepmania. I get the following output at the end 
```

checking for mad_synth_init in -lmad... no
configure: error: A working installation of MAD could not be found, which is
required for MP3 support.  If you really want to compile without MP3 support,
pass the "--without-mp3" flag to configure.
```

What package is that referring to? I tried googling around for it, but I cant seem to find it

---

### Post by schorsch on 2007-11-04
I guess you are missing the libmad0-dev package. You can install it via
```
sudo aptitude install libmad0-dev
```

---

### Post by Sir_Sid on 2007-11-04
thanks that was it

---

