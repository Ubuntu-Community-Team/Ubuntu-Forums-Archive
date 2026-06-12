---
title: "How to Compile a program in VI editor in Terminal?"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-16
How to Compile a program in VI editor in Terminal?

---

### Post by jordanmthomas on 2008-02-16
I'm sure it's possible since vi is nearly an OS in itself (that's a joke) but typically you don't compile programs inside of a text editor.

What is the program you're trying to compile?

---

### Post by spiderbatdad on 2008-02-16
use vim

---

### Post by PeterJS on 2008-02-16
No use emacs! :)

Sorry couldn't resist.

---

### Post by Whiffle on 2008-02-16
I just open up another terminal in the same directory and compile it there, no need to close vim to do it.  I'm not aware of any way to make  vim compile it actually, although it wouldn't surprise me.

---

### Post by peabody on 2008-02-16
Criminey, I'm an Emacs user and even I know this much folks :).

two methods:

1) [the "right" way] create a basic makefile something like

```

all:
      gcc -o prog prog.c

```

then run :make

This has the advantage that if you have any compilation errors, you can skip through them in your error list with :cnext and :cprevious.  No need to futs with line numbers.

2) [The quick and dirty way]  Just do :!gcc -o prog prog.c

:! is the command to use to run a shell command from within vi/m.

---

