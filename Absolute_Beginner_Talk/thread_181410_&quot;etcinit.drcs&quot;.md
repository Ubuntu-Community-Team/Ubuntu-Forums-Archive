---
title: "&quot;etc/init.d/rcs&quot;"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by quixotix on 2006-05-24
I've been using Ubuntu 5.10 now for a few days I only installed Konqueror and Amorok from the 'add applications' and have been very happy, untill yesterday when booting I got the message ' cannot execute "etc/init.d/rcs" entering runlevel 2 "etc /init.d/rcs". I ended up reinstalling, does anyone know what went wrong?

---

### Post by savas on 2006-05-24
[QUOTE=quixotix]I've been using Ubuntu 5.10 now for a few days I only installed Konqueror and Amorok from the 'add applications' and have been very happy, untill yesterday when booting I got the message ' cannot execute "etc/init.d/rcs" entering runlevel 2 "etc /init.d/rcs". I ended up reinstalling, does anyone know what went wrong?[/QUOTE]

This script used by init to boot system. Probably, you damaged this script or other script that init uses to boot system. Reinstall will solve this problem.

---

