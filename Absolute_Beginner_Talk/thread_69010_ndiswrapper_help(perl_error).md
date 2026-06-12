---
title: "ndiswrapper help(perl error)"
date: 2005-09-25
forum: Absolute Beginner Talk
---

### Post by CoFFeY on 2005-09-25
Ok, i hook my computer to ethernet and installed ndiswrapper and when i did it i got this error that says


perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information

please help

---

### Post by byen on 2005-09-26
listen dude... many have tried and gone through a lot of trouble with ndiswrapper. and there is one place i strongly suggest you visit [<<<click here>>>]("http://www.ubuntuforums.org/showthread.php?t=25683")

Hope that helps....try it out.Goodluck. And since this is your 2nd post! Welcome to Ubuntu!

---

### Post by mlomker on 2005-09-26
> LANGUAGE = "en",

Try **dpkg-reconfigure locales** and select the one(s) that you use and remove the others.

---

