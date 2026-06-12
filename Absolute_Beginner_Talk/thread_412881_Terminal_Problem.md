---
title: "Terminal Problem"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Patsy on 2007-04-18
Hi

All of a sudden when I try and do a sudo command ,at the prompt for password I am unable to type anything in at all.  The keys just don't enter on the screen.

Hoping someone can help me please?

---

### Post by yabbadabbadont on 2007-04-18
If you just hit Enter, does it tell you that the password is invalid and prompt you again?

---

### Post by freebird54 on 2007-04-18
Not a problem after all.  When you are entering a password for sudo, it does NOT echo.  This is intentional.  Go ahead and type it in and hit enter.  If you type it correctly, the command works - if not, it tells you that too.

Confuses a few people I know - but because it uses a 'readLINE' rather than a 'readcharacter' it can't echo *** to you.

Relax and enjoy!

---

### Post by Patsy on 2007-04-18
> **yabbadabbadont said:**
> If you just hit Enter, does it tell you that the password is invalid and prompt you again?


Hiya

No, it seems to be what Freebird said so problem sorted:)

---

### Post by Patsy on 2007-04-18
> **freebird54 said:**
> Not a problem after all.  When you are entering a password for sudo, it does NOT echo.  This is intentional.  Go ahead and type it in and hit enter.  If you type it correctly, the command works - if not, it tells you that too.

Confuses a few people I know - but because it uses a 'readLINE' rather than a 'readcharacter' it can't echo *** to you.

Relax and enjoy!

Thanks Freebird, it was driving me insane almost!

---

### Post by yabbadabbadont on 2007-04-18
> **Patsy said:**
> Hiya

No, it seems to be what Freebird said so problem sorted:)

That's what I was getting at.  I wanted to make sure that the keyboard was actually working at the password prompt before I went into details on how the command line password prompt worked.  As long as you got the correct answer and everything is working, that's what counts.  :D

---

