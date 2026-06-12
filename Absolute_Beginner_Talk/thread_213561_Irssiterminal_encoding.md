---
title: "Irssi/terminal encoding"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Kurt` on 2006-07-11
Hi,

I need Irssi 0.8.10 (20051211) to be able to display Finnish characters properly. I know that I need to change the term_charset variable via /set.

How do I determine which encoding this falls under? Looking at the [Wikipedia entry](http://en.wikipedia.org/wiki/Finnish_language) for the Finnish language, I found that it uses:

ISO 639-1
ISO 639-2
ISO/DIS 639-3

... whatever that means. :p

Wouldn't this fall under a "group" encoding such as "latin1" or something similar?

Also, shouldn't UTF-8 be able to handle ANYTHING? With UTF-8 set, I can't display German umlauts, or even Cyrillic script correctly. Is that a limitation of my IRC client, or my terminal program? If so, how can I internationalize my system? :)

I seem to remember a dpkg-configure command to control what locales were installed, but I don't remember if that had anything to do with this or not.

Thanks in advance

---

### Post by fluffington on 2006-07-12
You should be using the same character set as whoever you're talking to. UTF-8 is pointless (and will result in lots of garbage on someone's display) if the person you're talking to is using something else, e.g. Western/Latin 1 (ISO 8859-1). You also need to be using a character set supported by whatever server you're connected to (Unicode support is rare, but I've seen all kinds of other sets).

As far as Irssi's capabilities go, I don't know (I've never used it), but you might want to make sure whatever font you're using contains all of the characters you're trying to display.

---

