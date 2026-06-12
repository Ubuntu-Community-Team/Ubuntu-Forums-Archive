---
title: "How is BSD allowed to distribute GPL code?"
date: 2008-06-04
forum: BSD
---

### Post by Luke has no name on 2008-06-04
Tons of their packages are GPL based, how are they allowed to ship BSD with that code?

OR, is the core BSD system purely BSD (or similar) licensed, and the only GPL software are extras?

---

### Post by cammin on 2008-06-05
It doesn't matter as long as they comply with the licensing terms. 

[http://www.openbsd.org/policy.html](http://www.openbsd.org/policy.html)
[http://www.netbsd.org/about/redistribution.html](http://www.netbsd.org/about/redistribution.html)

"FreeBSD is released under a variety of licenses. The kernel code and most newly created code is released under the two-clause BSD license which allows everyone to use and redistribute FreeBSD as they wish. There are parts under the GPL, LGPL, ISC, CDDL and Beerware licenses, along with three- and four-clause BSD licenses. Some device drivers include a binary blob, such as the Atheros HAL."

---

### Post by Luke has no name on 2008-06-05
> **cammin said:**
> It doesn't matter as long as they comply with the licensing terms. 

[http://www.openbsd.org/policy.html](http://www.openbsd.org/policy.html)
[http://www.netbsd.org/about/redistribution.html](http://www.netbsd.org/about/redistribution.html)

"FreeBSD is released under a variety of licenses. The kernel code and most newly created code is released under the two-clause BSD license which allows everyone to use and redistribute FreeBSD as they wish. There are parts under the GPL, LGPL, ISC, CDDL and Beerware licenses, along with three- and four-clause BSD licenses. Some device drivers include a binary blob, such as the Atheros HAL."

I thought that GPL couldn't be redistributed with other licenses.

---

### Post by cardinals_fan on 2008-06-05
> **Luke has no name said:**
> I thought that GPL couldn't be redistributed with other licenses.
It isn't.  All GPLed code in any BSD distrobution is licensed under the GPL, not the BSD license.

---

### Post by Bachstelze on 2008-06-06
> **Luke has no name said:**
> 
OR, is the core BSD system purely BSD (or similar) licensed, and the only GPL software are extras?

Bingo.

---

### Post by Luke has no name on 2008-06-10
> **cardinals_fan said:**
> It isn't.  All GPLed code in any BSD distrobution is licensed under the GPL, not the BSD license.


What I meant was: I thought that GPL code could not be distributed alongside BSD code. However, I think Hymn answered the question.

---

### Post by Bachstelze on 2008-06-11
> **Luke has no name said:**
> What I meant was: I thought that GPL code could not be distributed alongside BSD code. However, I think Hymn answered the question.

Yap ;) Actually, pretty much every UNIX-like OS on the planet distributes BSD and GPL code together (OpenSSH, Xorg, Apache, etc. are BSD-licensed pieces of software that virtually every UNIX-like OS has "packages" for). What is forbidden, however, is to use GPL code in a non-GPL project (without authorization from the author), so, for example, GPL code cannot be used in Xorg. But it is very possible to distribute them alongside each other, if they are kept separate.

---

