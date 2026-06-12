---
title: "latest firefox update (always crashes)"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by vronp on 2007-10-23
Hi all,

This morning I noticed the new firefox update and installed it.  Well, now I can't even load all my previously saved web pages.  Firefox just crashes.

What is the best way to back up one revision level?  I'd like to get back to what I had yesterday.

thanks

---

### Post by Seisen on 2007-10-23
Open up firefox in the terminal post the error message.

---

### Post by vronp on 2007-10-23
firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
/usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/firefox/components/libmyspell.so: undefined symbol: _ZN8Hunspell5spellEPKc

---

### Post by kamitsukai on 2007-10-23
hmmm...i installed that update with no problems

---

### Post by vronp on 2007-10-23
I suspect that only certain types of web pages trigger this error.

---

### Post by Seisen on 2007-10-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hunspell/+bug/111940](https://bugs.launchpad.net/ubuntu/+source/hunspell/+bug/111940) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Which version of libhunspell do you have installed?  Type this in the terminal

```
libhunspell --version
```

---

### Post by vronp on 2007-10-23
That command is not found but I looked in synaptic and the installed version is 1.1.5-6

By the way, and this is a general question, what is the best way to go to a previous version of a package like libhunspell or firefox ???


> **Seisen said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hunspell/+bug/111940](https://bugs.launchpad.net/ubuntu/+source/hunspell/+bug/111940) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Which version of libhunspell do you have installed?  Type this in the terminal

```
libhunspell --version
```

---

### Post by Seisen on 2007-10-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/107340](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/107340) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Check this bug report out it lists to different ways to fix the problem, I actually 
linked the wrong bug report in my last post this is the right one for the problem you are having.

---

### Post by vronp on 2007-10-23
I found a workaround.  If you uncheck "spell as I type" in the Advanced preferences then it doesn't crash.

---

### Post by vronp on 2007-10-23
How does one downgrade a package?

---

### Post by alienexplorers on 2007-10-24
Try this:
> [http://kb.mozillazine.org/Problematic_extensions](http://kb.mozillazine.org/Problematic_extensions)

---

### Post by vronp on 2007-10-24
That is a useful web site but it is entirely unrelated to this particular problem.


> **alienexplorers said:**
> Try this:

---

### Post by verymagicalguy on 2007-11-01
My firefox does this as well. I updated to 2.0.0.8 and it won't stay open for more than 5 minutes. I'm using Opera for now.

---

