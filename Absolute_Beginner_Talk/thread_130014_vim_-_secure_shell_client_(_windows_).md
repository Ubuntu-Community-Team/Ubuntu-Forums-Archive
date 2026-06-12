---
title: "vim - secure shell client ( windows )"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by guerra on 2006-02-15
Hail all!

Anyone knows if its possible to use colors on vim when loggin via ssh from windows for instance?

The terminal has colors when i do a "ls" but when i vim somethin its always black and white, and my .vimrc is right.

Thanks in advance!

Take care all!

---

### Post by guerra on 2006-02-15
Hail all!

Anyone knows if its possible to use colors on vim when loggin via ssh from windows for instance?

The terminal has colors when i do a "ls" but when i vim somethin its always black and white, and my .vimrc is right.

Thanks in advance!

Take care all!

---

### Post by heimo on 2006-02-15
[quote=guerra]Anyone knows if its possible to use colors on vim when loggin via ssh from windows for instance?[/quote]

It is. I'm sure. What's your terminal type?
```
echo $TERM
```

I guess it should be already correct (as ls shows colors), but you can try:
```
TERM=xterm vi test.c
```
or
```
TERM=xterm-color vi test.c
```
(with the kind of file that you'd edit using colored syntax highlighting)

---

### Post by guerra on 2006-02-15
Yo man! many thanks, it worked!

But is there a way to make it permanent?

My terminal is: vt100

Thanks again!

Take care!

guerra

---

### Post by guerra on 2006-02-15
Forget it!

Its working pretty well!

Thanks a lot!

---

### Post by ibbuntu on 2008-01-22
Hi, I tried this and it worked, however when I do this my backspace key works like my delete key and vice-versa. Anyway to get round this?

Tom

---

