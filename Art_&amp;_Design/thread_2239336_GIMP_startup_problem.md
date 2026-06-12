---
title: "GIMP startup problem"
date: 2014-08-13
forum: Art &amp; Design
---

### Post by reismith on 2014-08-13
I have been experiencing a reoccurring problem starting up GIMP first under Ubuntu 12.04 and now under 14.04.1. If I attempt to execute from the icon, it simply fails to startup; no windows appear, no error messages. If I attempt a startup in the Terminal screen, I do see the startup screen, the Tip of the Day, and the tools window but get the following error message in the Terminal window:

/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:17391): LibGimpBase-WARNING **: gimp: wire_read(): error
/usr/local/lib/gimp/2.0/plug-ins/helpbrowser: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory

(gimp:17391): LibGimpBase-WARNING **: gimp: wire_read(): error

The application fails to fully open (no edit window).

I've tried uninstalling and reinstalling but it changes nothing. When I updated to 14.04.1, I did not have GIMP installed in 12.04 and reinstalled fresh in 14.04 but got the same result. Is what seems to be missing/corrupted part of the Linux kernel? I've been updating that all along as well. No other app is exhibiting a similar issue. Any idea how I can fix this?

---

### Post by steeldriver on 2014-08-13
Where did you get the 'print' and 'helpbrowser' plugins? their location (/usr/**local**/lib/gimp/2.0/plug-ins/print) suggests they're not a part of your standard GIMP distribution - or did you install a non-repo version of GIMP?

---

### Post by reismith on 2014-08-13
I have only done the standard GIMP installation, first under 12.04 (a few times), and last under 14.04. If those plugins are not in the standard location, not sure how they got where they are. But more importantly, how can this be fixed. As it is now, I can't seem to find a way to get GIMP running.

---

### Post by steeldriver on 2014-08-14
What are the outputs of

```

which gimp

dpkg -S /usr/local/lib/gimp

```

---

### Post by ofnuts on 2014-08-14
You can have problems with plugins on startup, this shouldn't prevent Gimp from starting (but the plugin will be disabled). However these problem can be just an indication of a more general problem.

In case of startup problems; the usual recommendation is to remove/disable your [Gimp profile]("http://gimpforums.com/thread-what-is-my-gimp-profile-and-where-do-i-find-it") by renaming it. Fixing your problem is not guaranteed but at least it will eliminate the hypothesis of something wrong in the profile (which from experience causes 95% of Gimp startup problems). Since the profile survives Gimp re-installations, any problem in it won't be fixed by reinstalling. 

Otherwise I agree with SteelDriver, your setup is weird, the plugins in a standard install are in /usr/lib/gimp/2.0/plug-ins/. Where did you install from? repository? ppa? local build?

---

### Post by reismith on 2014-08-15
Seemed to have fixed it. Deleted the current GIMP profile folders in /home which alone didn't solve the problem but then also removed GIMP related files and folders that were in /usr/local. Then an uninstall and reinstall seemed to have fixed the problem. Now I just have to learn how to use the program....

Thanks for all the suggestions. Got me started in the right direction.

---

### Post by steeldriver on 2014-08-15
Glad you got it fixed - please take time to mark the thread as [SOLVED]

---

### Post by ofnuts on 2014-08-15
> **reismith said:**
> Now I just have to learn how to use the program.....

[GIMP Forums - A Friendly Community of GIMP Users]("http://gimpforums.com/")

Wink, wink, nudge, nudge....

---

