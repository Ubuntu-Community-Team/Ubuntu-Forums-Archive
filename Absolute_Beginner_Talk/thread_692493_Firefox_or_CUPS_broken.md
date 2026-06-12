---
title: "Firefox or CUPS broken?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by siddartha on 2008-02-09
Hello,

As I print using the virtual printer of CUPS from Firefox I discovered that the page count is ok, the page numbers are ok, the header and footer ar ok, yet the text is sinking from the first page to unknown depths unprinted by a PDF viewer while the other pages remain empty. Is there a solution?

Cheers,
Sidd

---

### Post by tyggna1 on 2008-02-10
if there is-- then you'll probably find it by playing around with the options listed (from an applications->accessories-> terminal window) from typing in one of these:
```

man cupsd
man cupsdconf
man cupsd.conf
man cupsfilter
```

---

### Post by siddartha on 2008-02-11
Your answer sounds like a wild goose chase. Made a simple test - printed the same page from Konqueror. And the resulting PDF is ok. It does not look like a CUPS problem. Just another broken feature of firefox.

Now, for my own curiosity, what were you trying to point by giving the list of man pages? The fact that you know what's the name of the cups configuration file?

---

