---
title: "Arch Forums Registration"
date: 2011-09-13
forum: Any Other OS
---

### Post by jhargis1012 on 2011-09-13
Hi. I've been a long-time Ubuntu user, and I wanted to give Arch a try as I've heard good things. This is kind of humorous, but I can't finish the forums registration over there because of an anti-spam protection they have setup. I'm still a Linux noob (one of the reasons why I wanted to try my hand at a difficult to use distro), so I don't understand what it's asking.

The question is as follows:

What is the output of "date -u +%W$(uname)|sha256sum|sed 's/\W//g'"?

What does that mean? When I type it into a terminal, I get a long line of letters and numbers that doesn't work as the answer.

Sorry about the ultra-noobish question!

---

### Post by sisco311 on 2011-09-13
date -u = print date and time UTC

+%W = print only week number of year

$(uname) = is substitueted with the output of the uname command

uname = prints system information, wihtout options prints the kernel name which is most likely Linux (not sure what's the output on OSX or Solaris or BSD)

sha256sum computes the checksum of the test returned by *date ...*

sed deletes some *garbage* from the end of the checksum.

This is the output I get:
215c772cdf8deea7be70200ac9bf92d938473697425b4d3d6914aa0428f5ba7e

If you are using Ubuntu & the system date and time is correct, then your should be the same.

---

### Post by haqking on 2011-09-13
> **jhargis1012 said:**
> Hi. I've been a long-time Ubuntu user, and I wanted to give Arch a try as I've heard good things. This is kind of humorous, but I can't finish the forums registration over there because of an anti-spam protection they have setup. I'm still a Linux noob (one of the reasons why I wanted to try my hand at a difficult to use distro), so I don't understand what it's asking.

The question is as follows:

What is the output of "date -u +%W$(uname)|sha256sum|sed 's/\W//g'"?

What does that mean? When I type it into a terminal, I get a long line of letters and numbers that doesn't work as the answer.

Sorry about the ultra-noobish question!


As answered informatively above me by Sisco.

you can also

```
man date
```

to get all the information you need on it using terminal

---

### Post by sisco311 on 2011-09-13
Oh, and Arch has a realy good Wiki, check it out, you will probaly find the answere for most of your questions there.

Before you post in the forum, check out: [https://wiki.archlinux.org/index.php/Forum_Etiquette](https://wiki.archlinux.org/index.php/Forum_Etiquette)

Or they will yell at you. j/k

---

### Post by jhargis1012 on 2011-09-13
Thank you for the help!

---

### Post by realzippy on 2011-09-14
> **jhargis1012 said:**
>  ..because of an anti-spam protection they have setup.
The question is as follows:

What is the output of "date -u +%W$(uname)|sha256sum|sed 's/\W//g'"?


...sounds more like a anti-noob protection.

---

### Post by Majorix on 2011-09-15
> **realzippy said:**
> ...sounds more like a anti-noob protection.

Wouldn't that be kinda elitist? I hope that wasn't on their mind with this.

---

