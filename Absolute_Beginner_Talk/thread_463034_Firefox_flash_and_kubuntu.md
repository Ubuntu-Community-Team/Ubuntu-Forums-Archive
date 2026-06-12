---
title: "Firefox flash and kubuntu"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by natman on 2007-06-03
Hi,
I have firefox running in kubuntu ( 64 ) but i run firefox32 so i can get all the extras. It used to work just fine, but now sites like youtube and yahoo messenger for web, are crashing it all the time. I preume its the flash content, cause i have the addon flash block, once i enable the flash content the window crashes can anyone help?
Also everything works fine under win vista.
I ran it in the terminal and got this
[HTML]natman@natman-laptop:~$ firefox32
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
esd: no process killed
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(firefox-bin:6845): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
Segmentation fault (core dumped)
natman@natman-laptop:~$ 
[/HTML]

---

### Post by shae on 2007-06-10
It seems firefox cannot find libpango.  Perhaps you should try running 
```
sudo apt-get install -f
```

---

### Post by fakie_flip on 2007-06-11
Why not use the nspluginwrapper to have flash in 64 bit Firefox? It worked just fine for me, and I'm glad I did not have to install a 32 bit Firefox.

---

