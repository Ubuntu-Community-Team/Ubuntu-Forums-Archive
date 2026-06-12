---
title: "adding packages"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by cong06 on 2007-06-01
I feel terrible about asking this one simple question....but I can't seem to find it anywhere.

Easily anyway....

How do you add a package to the Package manager through the terminal? If I wanted to use GUI, I'd go:
System >> Administration >> Synaptic  Package Manager >> Settings >> Repositories >> Third-Party Software >> Add

and then just put the code: (for example)
```

deb http://apt.tt-solutions.com/ubuntu/ dapper main

```

but that takes too long.....what's the code for the terminal so I can save time when I do this next time?

---

### Post by taurus on 2007-06-01
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by cong06 on 2007-06-02
*sigh*
I knew it'd be something ridiculously simple.

thanks.

---

