---
title: "locale and case sensitivity: how to?"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by uqbar on 2006-05-19
Hi all again.
I'm running Kubuntu Dapper flight 6 with a national locale (it_IT@EURO).
I'd like to have back my case sensitivity in the shell while still retaining the national settings.
If I do "export LC_ALL=C", I get the sensitivity, but loose the national settings.
I've found the locale files in /usr/share/i18n/locales but have no clue on how to fix this problem.
Thanks in advance.

---

### Post by uqbar on 2006-05-19
[QUOTE=uqbar]
If I do "export LC_ALL=C", I get the sensitivity, but loose the national settings.
[/QUOTE]
Maybe I've found out the solution by myself.
On [http://www.debian.org/doc/manuals/intro-i18n/ch-locale.en.html]("http://www.debian.org/doc/manuals/intro-i18n/ch-locale.en.html") there is a nice introduction to the locale "problem".
At chapter 6 there is a technology explain.
I've used "export LC_COLLATE=C" instead so only collation gets turned back to the case sensitivity every Unix user expects.

In any case, I'd say that case insensitivity should be the default for every locale in a Unix-like environment. When you list a home directory contents, you'd lke to see the "dot files" at beginning, then capital case names and only at the end the lower case names.

---

### Post by flangemonkey on 2007-09-11
hello,

I too would like to restore case sensitivity to my shell, nto being a danger monkey I would like it very much if you could explain what the "export LC_ALL=C" and "export LC_COLLATE=C" are.

Looking at that link you submitted it merely shows locale settings (mine refers to "en_GB.UTF-8") - is this where the changes should be made?

thanks for your time,

Phill

---

