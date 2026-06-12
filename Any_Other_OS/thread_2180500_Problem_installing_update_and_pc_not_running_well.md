---
title: "Problem installing update and pc not running well"
date: 2013-10-13
forum: Any Other OS
---

### Post by Darkchild101 on 2013-10-13
I tried to instal updates and got this message below. In general the pc is not running well behaves the way a Windows based pc would when riddled with a trojan/virus. Videos freeze when playing and sometimes pages take a tad too long to load. I know Linux cant get infected so what could be causing this. Sometimes the pc is not responsive at all and then i get a message about a script running and if i want to stop it :mad:

Here is the message i got when installing updates




Failed to fetch  [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Something  wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address  associated with hostname)
Failed to fetch  [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)   Something wicked happened resolving 'packages.medibuntu.org:http' (-5 -  No address associated with hostname)
Failed to fetch  [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)   Something wicked happened resolving 'packages.medibuntu.org:http' (-5 -  No address associated with hostname)
Failed to fetch  [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_GB](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_GB)   Something wicked happened resolving 'packages.medibuntu.org:http' (-5 -  No address associated with hostname)
Failed to fetch  [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)   Something wicked happened resolving 'packages.medibuntu.org:http' (-5 -  No address associated with hostname)
Failed to fetch  [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_GB](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_GB)   Something wicked happened resolving 'packages.medibuntu.org:http' (-5 -  No address associated with hostname)
Failed to fetch  [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)   Something wicked happened resolving 'packages.medibuntu.org:http' (-5 -  No address associated with hostname)
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ibjsb4 on 2013-10-13
You need to find a different flavor of ubuntu.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by david98 on 2013-10-13
I agree with [[COLOR=#000000]ibjsb4[/COLOR]]("http://ubuntuforums.org/member.php?u=1729120")[COLOR=#000000]  download and burn another copy of ubuntu depending on your system spec's i would use 12.04 lts. If you are using a older system try lubuntu perfect for older xp like system specs[/COLOR]

---

### Post by grahammechanical on 2013-10-13
So, this problem is nothing to do with the fact that Medibuntu no longer exists?

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Remove those repositories from your Software sources and the problem will no longer appear.

Regards

---

### Post by Bucky Ball on 2013-10-13
> **david98 said:**
> ... download and burn another copy of ubuntu ...

No. See below. Medibuntu repos have closed. Just remove the PPAs and all reference. 

> **grahammechanical said:**
> So, this problem is nothing to do with the fact that Medibuntu no longer exists?

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Remove those repositories from your Software sources and the problem will no longer appear.

Regards

Yes! ;)

---

### Post by ibjsb4 on 2013-10-13
> **grahammechanical said:**
> So, this problem is nothing to do with the fact that Medibuntu no longer exists?

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Remove those repositories from your Software sources and the problem will no longer appear.

Regards

Interesting.  Did not know that :)

DarkChild; could you post the output of:
```
cat /etc/apt/sources.list
```
Please post using ["code tags"]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")
[URL="https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal"]
https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal[/URL]

---

### Post by Darkchild101 on 2013-10-16
> **ibjsb4 said:**
> Interesting.  Did not know that :)

DarkChild; could you post the output of:
```
cat /etc/apt/sources.list
```
Please post using ["code tags"]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")
[URL="https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal"]
https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal[/URL]

```
deb http://packages.linuxmint.com/ maya main upstream import romeo backport
deb-src http://packages.linuxmint.com/ maya main upstream import romeo backport #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ precise partner
# deb http://packages.medibuntu.org/ precise free non-free

deb http://mirrors.dotsrc.org/getdeb/ubuntu precise-getdeb apps
deb-src http://mirrors.dotsrc.org/getdeb/ubuntu precise-getdeb apps

```

---

### Post by lunalui on 2013-10-16
thanks for this! I had the same problem and it's now fixed :)

---

### Post by Otto-C on 2013-10-16
Take a look at this thread.  May have to reboot when done.
[http://ubuntuforums.org/showthread.php?t=2180310&highlight=otto-c](http://ubuntuforums.org/showthread.php?t=2180310&highlight=otto-c)

hth

---

