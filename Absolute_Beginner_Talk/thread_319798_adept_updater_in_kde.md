---
title: "adept updater in kde"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by essendon on 2006-12-16
when I run the updater to get new packages, I get this error:

Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

I used the system monitor to see if there are any programs running it.  I couldn't find any other than adept_notifier.

Can somebody help me with this please.](*,)

---

### Post by garyinok on 2007-01-23
I found the solution in the apt handbook in Ch 7 "common errors" at the following link:

[http://www.debian.org/doc/manuals/ap...-erros.en.html](http://www.debian.org/doc/manuals/ap...-erros.en.html)

"If an installation breaks in the middle of the process and you find that it's no longer possible to install or remove packages, try running these two commands:

# apt-get -f install
# dpkg --configure -a

And then try again. [COLOR="Red"]It may be necessary to run the second of the above commands more than once.[/COLOR] This is an important lesson for those adventurers who use `unstable'.

Hope this helps

---

