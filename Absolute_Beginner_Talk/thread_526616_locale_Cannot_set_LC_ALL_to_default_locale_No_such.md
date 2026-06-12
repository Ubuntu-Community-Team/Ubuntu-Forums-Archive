---
title: "locale: Cannot set LC_ALL to default locale: No such file or directory"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by dgcarter on 2007-08-15
I'm trying to install Gnome desktop on my Linux Box, "apt-get install ubuntu-desktop"

But I'm getting this error when it installs the packages:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_ZA:en",
        LC_ALL = "en_ZA.UTF-8",
        LANG = "en_ZA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory

```

And running dpkg-reconfigure locales does not help, all I get is:

```
dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_ZA:en",
        LC_ALL = "en_ZA.UTF-8",
        LANG = "en_ZA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
Current default timezone: 'Africa/Johannesburg'.
Local time is now:      Thu Aug 16 00:00:35 SAST 2007.
Universal Time is now:  Wed Aug 15 22:00:35 UTC 2007.
Run 'tzconfig' if you wish to change it.

```


Please heeeeelp!!!
Thanks,
Darren

---

### Post by milosz.galazka on 2007-08-15
Hello, maybe first try **aptitude reinstall locales** and then reconfigure it, there is even package **locales-all**...

**locale -a**
Write names of available locales.

---

