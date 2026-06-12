---
title: "Need help with locales."
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Iesos on 2006-10-29
I have had several problems with locales since a long time back but they haven't bothered me until now.
These are some examples of error messages I get, because of my locales:

Running synaptic (or any other application):
```
$ sudo synaptic
Password:

(synaptic:5046): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
```

Running, for example, dpkg-reconfigure locales (or anything else related to apt-get or dpkg):
```
$ sudo dpkg-reconfigure locales
Password:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US.UTF-8",
        LC_ALL = (unset),
        LANG = "sv_SE"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
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
```

And, the worst thing, trying to access my 32-bit chroot enviornment (I'm on amd64):
```
$ dchroot -d
E: locale::facet::_S_create_c_locale name not valid
```

I have asked on both #ubuntu and #ubuntu-se for help, but noone seem to know enough about locales to help me. I got some tips though. One was to run
$ sudo dpkg-reconfigure locales
but that didn't help. All the same messages still shows.
Then, someone told me to
$ sudo apt-get install --reinstall locales
well, now after the second time I have gotten tired of that tip too.
Then someone told me to edit /etc/environment. My original /etc/environment was:
```
LANGUAGE="en_SE:en"

LANG="en_US.UTF-8"
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
```
and since I'm swedish and have a swedish keyboard I thought that the right options would be sv_SE. So I changed, no result. Did I do something wrong? How should this new /etc/environment look exactly?
I tried to change to en_US, everywhere. That should at least get rid of all these errors. Well, it didn't. One strange thing is, event though I had changed inte en_US, I still got the 
```
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US.UTF-8",
        LC_ALL = (unset),
        LANG = "sv_SE"
    are supported and installed on your system.
```
part (Observe: LANG = "sv_SE").

To summrize:
I want to reinstall my locales so I can get rid of these errors. I want to have support for the swedish letters åäö, but still have the english translation/version of ubuntu.

---

### Post by Iesos on 2006-10-29
I solved it!
I opened
```
$ sudo gedit /var/lib/locales/supported.d/local
```
and added those locales that was requested, that is, for me:
```
sv_SE.UTF-8 UTF-8
sv_SE UTF-8

```
then I ran
$ sudo dpkg-reconfigure locales
which fixed my errors.

---

### Post by BLTicklemonster on 2006-12-12
> **Iesos said:**
> I solved it!
I opened
```
$ sudo gedit /var/lib/locales/supported.d/local
```
and added those locales that was requested, that is, for me:
```
sv_SE.UTF-8 UTF-8
sv_SE UTF-8

```
then I ran
$ sudo dpkg-reconfigure locales
which fixed my errors.

Excellent! I've been looking for a solution for this!

---

### Post by Iarwain ben-adar on 2006-12-12
Added to my list aswell :D

Thanks for the heads-up!


Iarwain

---

