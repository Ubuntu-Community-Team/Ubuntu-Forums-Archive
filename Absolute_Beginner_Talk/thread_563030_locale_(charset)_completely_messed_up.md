---
title: "locale (charset) completely messed up"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-09-29
Hope someone will be able to help me. It doesn't seem like many people knows much about this issue. At least a lot of the pots on the topic is unanswered. But here mine, I have been trying to change the default locale setting on my ubuntu-server and in doing so I have completely messed everything up.

my /etc/environment
> -PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
        LANGUAGE = "da_DK ISO-8859-1",
        LC_ALL = "da_DK ISO-8859-1",
        LC_PAPER = "da_DK ISO-8859-1",
        LC_ADDRESS = "da_DK ISO-8859-1",
        LC_MONETARY = "da_DK ISO-8859-1",
        LC_NUMERIC = "da_DK ISO-8859-1",
        LC_TELEPHONE = "da_DK ISO-8859-1",
        LC_MESSAGES = "da_DK ISO-8859-1",
        LC_IDENTIFICATION = "da_DK ISO-8859-1",
        LC_COLLATE = "da_DK ISO-8859-1",
        LC_MEASUREMENT = "da_DK ISO-8859-1",
        LC_CTYPE = "da_DK ISO-8859-1",
        LC_TIME = "da_DK ISO-8859-1",
        LC_NAME = "da_DK ISO-8859-1",
        LANG = "da_DK ISO-8859-1"

my /var/lib/locales/supported.d/local
> da_DK.UTF-8
da_DK.ISO-8859-1
the outout of sudo dpkg-reconfigure locales
> sudo dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "da_DK ISO-88569-1",
        LC_ALL = "da_DK ISO-8859-1",
        LC_PAPER = "da_DK ISO-8859-1",
        LC_ADDRESS = "da_DK ISO-8859-1",
        LC_MONETARY = "da_DK ISO-8859-1",
        LC_NUMERIC = "da_DK ISO-8859-1",
        LC_TELEPHONE = "da_DK ISO-8859-1",
        LC_MESSAGES = "da_DK ISO-8859-1",
        LC_IDENTIFICATION = "da_DK ISO-8859-1",
        LC_COLLATE = "da_DK ISO-8859-1",
        LC_MEASUREMENT = "da_DK ISO-8859-1",
        LC_CTYPE = "da_DK ISO-8859-1",
        LC_TIME = "da_DK ISO-8859-1",
        LC_NAME = "da_DK ISO-8859-1",
        LANG = "da_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
Error: Bad entry 'da_DK.ISO-8859-1 '
Error: Bad entry 'da_DK.UTF-8 '
Generation complete.
Can anyone guide me through getting this cleaned up again?

---

### Post by kasperbs on 2007-09-29
I somehow managed to get it back up and running.. But this locale thing does my head right now, it's really annoying not being able to copy files with æøå in them

---

