---
title: "Wrong locale in console mode"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by YaronSh on 2008-02-05
Ive been searching for the solution but none found
 
I accidentally installed Dapper Drake Server 6.06 LTS with Hebrew keyboard...
 
The only way I can get my keyboard to work correctly with English is pressing the Alt Key...
 
All the tools im familiar with are tools to switch the locale for the X enviroments and therefor I can't find a solution for this
 
Another Error im experiencing is that I can only login using the Recovery mode in GRUB, the other way around make some sort of error to show up (<0>Kernel panic - Not Syncing: fatal exception in interrupt)
 
Even answering one of the problems can sure help a lot
 
Thanks in advance to all the helpers!

---

### Post by jw5801 on 2008-02-05
Hmm... is it that your terminal is displayed in Hewbrew? Or simply that the keyboard layout is wrong?

The language variable is set in "/etc/environment" The "locale" command will tell you what locale you're currently using. Mine looks like:
```
$ locale
LANG=en_AU.UTF-8
LC_CTYPE="en_AU.UTF-8"
LC_NUMERIC="en_AU.UTF-8"
LC_TIME="en_AU.UTF-8"
LC_COLLATE="en_AU.UTF-8"
LC_MONETARY="en_AU.UTF-8"
LC_MESSAGES="en_AU.UTF-8"
LC_PAPER="en_AU.UTF-8"
LC_NAME="en_AU.UTF-8"
LC_ADDRESS="en_AU.UTF-8"
LC_TELEPHONE="en_AU.UTF-8"
LC_MEASUREMENT="en_AU.UTF-8"
LC_IDENTIFICATION="en_AU.UTF-8"
LC_ALL=
```
Where en_AU is English/Australia and UTF-8 is the charset. If /etc/environment sets everything correct and locale returns something sensible, then I'm not sure where else to set the keyboard layout. Normally I would think it would be in /etc/X11/xorg.conf, but obviously not in a server install!

---

### Post by jw5801 on 2008-02-05
Further info!
Another place to look is the /var/lib/locales/supported.d/local file, which should tell the system what locale it should be using (or an alternative should a program not have the first available). Or a good old fashioned ```
sudo dpkg-reconfigure locales
``` might do the trick.

As for the kernel panic, not sure about that one. Possibly because the system is trying to use a locale that isn't installed? No idea! Since this is a fairly new install, starting again from scratch might not be a bad option.

---

