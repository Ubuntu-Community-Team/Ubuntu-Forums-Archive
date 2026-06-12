---
title: "Errors with Xorg - related to blank boot screen??"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by taseedorf on 2008-01-15
I have the output of some commands showing
taseedorf@taseedorf-laptop:~$ cat /var/log/Xorg.0.log | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
taseedorf@taseedorf-laptop:~$ cat /var/log/Xorg.0.log | grep '(WW)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) LoadModule: given non-canonical module name "glesx.so"
taseedorf@taseedorf-laptop:~$ 
taseedorf@taseedorf-laptop:~$ cat /var/log/Xorg.0.log.old | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
taseedorf@taseedorf-laptop:~$ cat /var/log/Xorg.0.log.old | grep '(WW)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) LoadModule: given non-canonical module name "glesx.so"
taseedorf@taseedorf-laptop:~$ 


What do these errors mean? And how can I fix them?!?!?! I think they would fix my problems!

---

### Post by sauronsmatrix on 2008-01-18
errr.... that looks messy. try booting into recovery mode and use it to try and autoconfigure X

---

