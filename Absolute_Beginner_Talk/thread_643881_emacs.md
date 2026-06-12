---
title: "emacs"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2007-12-18
When I installed emacs, I typed: sudo apt-get install emacs.

Now when I run emacs, I get another window open with the X version of emacs, I want the old school terminal version. How can I get this?

Thanks,

---

### Post by Anicka on 2007-12-18
Install the package emacs-nox instead.

---

### Post by RomeReactor on 2007-12-18
Hi. Since you already have Emacs installed, try running it like this:
```
emacs -nw
```

---

### Post by CyberBob on 2007-12-18
You can also open a virtual console (Alt-F2, Alt-F3, etc.) and just type:

```
$ emacs
```

... and you will get the "old school terminal version."

---

