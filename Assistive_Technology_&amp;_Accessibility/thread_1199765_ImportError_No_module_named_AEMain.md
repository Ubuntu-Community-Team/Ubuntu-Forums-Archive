---
title: "ImportError: No module named AEMain"
date: 2009-06-29
forum: Assistive Technology &amp; Accessibility
---

### Post by aluget on 2009-06-29
Hi there. I tried to install LSR and when I run it via the terminal I get the following error message
 File "/usr/local/bin/lsr", line 28, in <module>
    import AEMain
ImportError: No module named AEMain 
Does anyone know how to overcome this error?
Thanks in advance

---

### Post by aluget on 2009-06-30
Bump

---

### Post by littlemog on 2009-11-06
Hi,

I encountered the same problem while trying to build from a checkout of LSR for a project. Basically when I run make install, I get the error that AEMain is missing.

checking the traceback got me to the root of the error that /usr/local/..bin/lsr is looking for 'site-packages', while on Ubuntu, the modules folder is in 'dist-packages'.

Just cd to the 'src' folder and run 'sudo vi lsr' after running 'make', and change it to point to 'dist-packages' and run make install.

works for me. :D

---

