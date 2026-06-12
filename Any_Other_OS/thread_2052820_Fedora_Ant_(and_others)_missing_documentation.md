---
title: "Fedora Ant (and others) missing documentation"
date: 2012-09-04
forum: Any Other OS
---

### Post by gardnan on 2012-09-04
I tried to install Apache Ant and some other Java related development files on a Fedora machine the other day, and tried to access their man pages.

However, I couldn't find them, not even after running mandb. Querying the package with the rpm tool listed no manual files in the package. I searched for a separate documentation package, but there was none.

This is all true with other packages as well (jetty, antlr).

Does Fedora just not support documentation for these packages?

---

### Post by gardnan on 2012-09-04
Well, I think I solved part of my problem.

There is an Ant manual package, but it provides a much fuller, HTML ant walkthrough, not the quick reference I was looking for.

The thread remains open to anyone who knows where to find and install the manpages.

---

### Post by UltimateCat on 2012-10-14
The man pages should be in your terminal.

Open the terminal and type:
```
man man

```OR:
```
man --help

```

Here's Fedora's main page and the release notes-
[http://fedoraproject.org/](http://fedoraproject.org/)
[http://docs.fedoraproject.org/en-US/Fedora/17/html/Release_Notes/](http://docs.fedoraproject.org/en-US/Fedora/17/html/Release_Notes/)

HTH

---

### Post by gardnan on 2012-10-14
Thanks for responding, but I knew how to access man pages from the terminal, but they just weren't installed with the packages on Fedora.

However, I have realized that I have probably left this thread open for too long, so now I am going to mark it as solved.

---

