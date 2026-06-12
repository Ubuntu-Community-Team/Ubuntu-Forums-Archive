---
title: "Change MAN language  in terminal"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by mafsi on 2007-11-26
hi,

when i need some help i type in terminal $ man whatsoever and i get the help in english. i want to change this in my language. how can i achive this?

thanks

---

### Post by marinesrock.1990 on 2007-11-26
Yeah, try this link:

[http://www.linuxquestions.org/questions/red-hat-31/changing-default-language-from-command-line-438947/]("http://www.linuxquestions.org/questions/red-hat-31/changing-default-language-from-command-line-438947/")

---

### Post by mafsi on 2007-11-26
> **marinesrock.1990 said:**
> Yeah, try this link:

[http://www.linuxquestions.org/questions/red-hat-31/changing-default-language-from-command-line-438947/]("http://www.linuxquestions.org/questions/red-hat-31/changing-default-language-from-command-line-438947/")

:confused:

sorry but i don't know exactly what to do...

---

### Post by bapoumba on 2007-11-26
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=manpages&searchon=names&subword=1&version=gutsy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=manpages&searchon=names&subword=1&version=gutsy&release=all")
Please look if there is a package for man pages in your preferred language. Note that not all man pages are translated.

---

### Post by Jadd on 2007-11-28
So, say you want man pages in french. First install them:
```
sudo apt-get install manpages-fr manpages-fr-extra manpages-fr-dev
```
Then view a man page, say the man page for man:
```
man -L fr_FR.UTF-8 man
```
or this one works as well:
```
man -L fr_FR.UTF-8 cp
```
However, not all french manpages are provided, example:
```
man -L fr_FR.UTF-8 firefox
```
This command:
```
sudo locale-gen
```
Will display a list of all the locale (languages) you have installed (as well as update them, it seems).
That's what my 15 minute research came up with, I hope some-else can explain a bit more, especially about what update-locale is all about.

---

### Post by mafsi on 2007-11-28
thanks a lot for your informations.

i asked on my language forum and the guys told me that it seems that future translations of manpages in my languages will approach to 0 :(

i think i'll skip the change & i will let it in english

---

