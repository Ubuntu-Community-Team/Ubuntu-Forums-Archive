---
title: "PLEASE fix the locales bug &quot;perl: warning: Setting locale failed&quot; once and for all??!"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by stormfrog on 2007-11-14
Ever since I started using Ubuntu locales has always been bugged. Ive tried every possible solution Ive found but none work, and most threads about this on Ubuntu are ignored for some reason.

It is a locales bug.

_Feedback and what Ive done so far:_
[LIST]
[*]sudo dpkg-reconfigure locales
[*]sudo apt-get install language-pack-en-base
[*]sudo apt-get install language-pack-sv-base
[/LIST]

[B]
cat /var/lib/locales/supported.d/local[/B]
```
sv_SE.UTF-8 UTF-8
sv_SE UTF-8
```

**cat /var/lib/locales/supported.d/en**
```
en_HK.UTF-8 UTF-8
en_DK.UTF-8 UTF-8
en_IN UTF-8
en_ZW.UTF-8 UTF-8
en_NZ.UTF-8 UTF-8
en_PH.UTF-8 UTF-8
en_US.UTF-8 UTF-8
en_GB.UTF-8 UTF-8
en_AU.UTF-8 UTF-8
en_SG.UTF-8 UTF-8
en_BW.UTF-8 UTF-8
en_ZA.UTF-8 UTF-8
en_CA.UTF-8 UTF-8
en_IE.UTF-8 UTF-8

```

**cat /var/lib/locales/supported.d/sv**
```
sv_SE.UTF-8 UTF-8
sv_FI.UTF-8 UTF-8
```

**cat /etc/default/locale**
```
LANG="sv_SE.UTF-8",
LANGUAGE="sv_SE.UTF-8",
LC_ALL="sv_SE.UTF-8"
```


**cat /etc/environment**
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="sv_SE.UTF-8",
LC_ALL="sv_SE",
LANG="sv_SE"
```

**dpkg-reconfigure locales**
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "sv_SE.UTF-8",",
        LC_ALL = "sv_SE.UTF-8",",
        LANG = "sv_SE.UTF-8"
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
  sv_FI.UTF-8... up-to-date
  sv_SE.UTF-8... up-to-date
  sv_SE.UTF-8... up-to-date
Generation complete.

```

I am insanely tired and annoyed by this and I wish someone would put an end to this question error so many seems to be having - once and for all!

---

### Post by gumbl on 2007-11-16
Hi
Strangely enough (I am trying the ISO-8859-1 standard) with your settings and, before I was as frustrated about things as you seem to be, but with your settings combined with the ISO-8859-1 standard seems to work perfect for me.

åäö works splendidly.

Some friends of mine seem to want convert the world to be using the utf-8 standard and sure... it may be the future.. but it's not the everyday standard today.
I have been getting confirmation throughout several im apps that the encoding is as it should.

---

