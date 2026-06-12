---
title: "changing console colors"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by lindos on 2006-06-04
hi how do i turn off the gdm and after that how do i change the background and foreground colours of the console:-k

---

### Post by Ecthelion on 2006-06-04
start the console
then click on edit/configure (or however it is called, the second menu on top)
click on profiles
click on the default and then change
or make a new profile

the you hve tabs with the colors/background etc

---

### Post by lindos on 2006-06-04
[QUOTE=Ecthelion]start the console
then click on edit/configure (or however it is called, the second menu on top)
click on profiles
click on the default and then change
or make a new profile

the you hve tabs with the colors/background etc[/QUOTE]
DUDE i know thai, I am asking about changing the console colors when the Graphical Display Manager or GDM is off

---

### Post by frenkel on 2006-06-04
[QUOTE=lindos]hi how do i turn off the gdm and after that how do i change the background and foreground colours of the console:-k[/QUOTE]
To disable GDM run this:
> sudo find /etc/rc?.d/ -name "*gdm*" -exec rm '{}' \;

Good luck,
Frank

---

### Post by lindos on 2006-06-04
[QUOTE=frenkel]To disable GDM run this:


Good luck,
Frank[/QUOTE]
And then how do i change the background and foreground colors

---

### Post by 5-HT on 2006-06-05
[quote=lindos]And then how do i change the background and foreground colors[/quote]
If in doubt, RTM ;):

[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/)
[http://www.gentoo.org/doc/en/articles/prompt-magic.xml](http://www.gentoo.org/doc/en/articles/prompt-magic.xml)

I'm not sure about the background though.

Hope that helps.

---

