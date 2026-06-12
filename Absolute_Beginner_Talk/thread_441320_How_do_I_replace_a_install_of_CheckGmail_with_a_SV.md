---
title: "How do I replace a install of CheckGmail with a SVN"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by SnowPunk98 on 2007-05-12
I downloaded a SVN from their site and made it executable. I can run it from a console by doing ./CheckGmail but I want to run it at startup. Can someone tell me how to overwrite the already installed one that I got from the Ubuntu repository and use this one?

---

### Post by FuturePast on 2007-05-12
Well, certainly the simplest way would be ```
$ sudo cp CheckGmail /usr/bin/checkgmail
```

---

### Post by RTrev on 2007-05-12
> **SnowPunk98 said:**
> I downloaded a SVN from their site and made it executable. I can run it from a console by doing ./CheckGmail but I want to run it at startup. Can someone tell me how to overwrite the already installed one that I got from the Ubuntu repository and use this one?

Have you tried Synaptic "Mark for complete removal"?  Then, with the new one set up somewhere, go into the System menu, Preferences, Sessions, and add the command to start in in the section called "Startup Programs".

I think.  :)

---

### Post by SnowPunk98 on 2007-05-12
> **FuturePast said:**
> Well, certainly the simplest way would be ```
$ sudo cp CheckGmail /usr/bin/checkgmail
```

That was it, thanks, I didn't know the home dir for it.

---

### Post by josephus on 2007-05-13
you can find out where your installed files are by looking in synaptic under Package->properties->installed files or using 'which <executable filename>'

---

