---
title: "Who and TTY"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Mramius on 2007-12-16
When I use the finger utility I see 
```

mramius      Mramius      *tty1       4d  Dec 11 23:06
mramius      Mramius       tty7           Dec 14 18:12 (:0)
mramius      Mramius       pts/0          Dec 14 18:52 (:0.0)
mramius      Mramius       pts/1      1d  Dec 14 20:40 (:0.0)
```

A few questions...

Why am I listed 4 times?
What is TTY?
What is PTS?

---

### Post by deepank on 2007-12-16
TTY : Stands for a character terminal device. 
PTY : It is a pseudo terminal i.e a terminal which is not actually there. 

You are being shown 4 times because you are working from all 4 of these terminals. Some of these might not be active on your desktop but they will be opened internally.

---

### Post by Dr Small on 2007-12-16
```
mramius      Mramius      *tty1       4d  Dec 11 23:06
```
That means you are logged in on VT1.

```
mramius      Mramius       tty7           Dec 14 18:12 (:0)
```
That means you are logged in on VT7. (Your default display terminal.)

```
mramius      Mramius       pts/0          Dec 14 18:52 (:0.0)
mramius      Mramius       pts/1      1d  Dec 14 20:40 (:0.0)
```
That means you have logged into the terminal, while on another terminal, twice; And didn't properly close them, because they are still open.

---

