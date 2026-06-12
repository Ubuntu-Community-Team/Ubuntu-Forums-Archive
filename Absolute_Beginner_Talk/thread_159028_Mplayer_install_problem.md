---
title: "Mplayer install problem"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by finch on 2006-04-12
Here what i get when try to install MPlayer-1.0pre7try2
```

root@finch:/home/finch/apps/MPlayer-1.0pre7try2# ./configure
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.0.2, bad
Checking for gcc version ... 4.0.2, bad
Checking for gcc-3.4 version ... 3.4.5, ok
Checking for host cc ... gcc-3.4
Checking for CPU vendor ... AuthenticAMD (6:8:1)
Checking for CPU type ...  AMD Athlon(tm) XP 1500+
Checking for GCC & CPU optimization abilities ... Your gcc-3.4 does not even support "i386" for '-march' and '-mtune'.
error
Checking for kernel support of mmx ... failed
It seems that your kernel does not correctly support mmx.
To use mmx extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of mmx2 ... failed
It seems that your kernel does not correctly support mmx2.
To use mmx2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of 3dnow ... failed
It seems that your kernel does not correctly support 3dnow.
To use 3dnow extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of 3dnowex ... failed
It seems that your kernel does not correctly support 3dnowex.
To use 3dnowex extensions in MPlayer, you have to upgrade/recompile your kernel!Checking for kernel support of sse ... failed
It seems that your kernel does not correctly support sse.
To use sse extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for mtrr support ... yes
Checking for assembler support of -pipe option ... no
Checking for assembler (as 2.16.1) ... ok
Checking for Linux kernel version ... 2.6.12-9-386, ok
Checking for mplayer binary name ... mplayer
Checking for awk ... mawk
Checking for extra headers ... none
Checking for extra libs ... none
Checking for -lposix ... no
Checking for -lm ... no
Checking for i18n ... no
Checking for iconv ... no
Checking for langinfo ... no
Checking for language ... using en (man pages:  en)
Checking for enable sighandler ... yes
Checking for runtime cpudetection ... no
Checking for restrict keyword ... none
Checking for __builtin_expect ... no
Checking for kstat ... no
Checking for posix4 ... no
Checking for lrintf ... no
Checking for nanosleep ... no
Checking for socklib ... no
Checking for inet_pton() ... no (=> i'll try inet_aton next)
Checking for inet_aton() ... no (=> network support disabled)
Checking for inttypes.h (required) ... no
Checking for bitypes.h (inttypes.h predecessor) ...
Error: Cannot find header either inttypes.h or bitypes.h (see DOCS/HTML/en/faq.html).

Check "configure.log" if you do not understand why it failed.

```
Where the problem could be?

---

### Post by xyz on 2006-04-12
"Patrick" wrote a very helpful howto solve multimedia pbms.
It might just come in handy for you as it did for me.
[http://www.ubuntuforums.org/showthread.php?t=157589](http://www.ubuntuforums.org/showthread.php?t=157589)

---

