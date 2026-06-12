---
title: "gcc includes"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by jim h on 2007-02-02
I saw that I had gcc, so I thought I was okay, but according to gcc and locate, I do not have the normal includes.  Could anyone suggest the most graceful way to get them for 6.10?
  Thanks very much in advance.
  Jim

---

### Post by po0f on 2007-02-02
jim h,

Ooh, ooh, I know this one!  Pick me!

```
[FONT="Courier New"]$ sudo aptitude install build-essential[/FONT]
```

---

### Post by jim h on 2007-02-02
That was indeed graceful, and many thanks.  Now a little diceyer -- how about X11?
  Thanks a ton in any case, and I have archived your elegant solution.

---

### Post by po0f on 2007-02-02
jim h,

Install [libx11-dev](http://packages.ubuntu.com/edgy/libdevel/libx11-dev).  You might also need [xserver-xorg-dev](http://packages.ubuntu.com/edgy/x11/xserver-xorg-dev) as well.

[EDIT]

Nevermind, it looks like you are actually looking for [xorg-dev](http://packages.ubuntu.com/edgy/x11/xorg-dev).

---

### Post by yabbadabbadont on 2007-02-02
sudo aptitude install xorg-dev

Edit: I'm just too slow tonight.  :D  (My answer pulls in more stuff though :p)

---

### Post by po0f on 2007-02-02
yabbadabbadont,

I was editing my reply as you were posting, it looks like.  ;)

---

### Post by jim h on 2007-02-02
> **po0f said:**
> jim h,

Install [libx11-dev](http://packages.ubuntu.com/edgy/libdevel/libx11-dev).  You might also need [xserver-xorg-dev](http://packages.ubuntu.com/edgy/x11/xserver-xorg-dev) as well.

[EDIT]

Nevermind, it looks like you are actually looking for [xorg-dev](http://packages.ubuntu.com/edgy/x11/xorg-dev).

  Thanks yet again.  This looks like a thing not to pursue at 2:45AM, so I will go after it tomorrow.  I really appreciate your help, here.
  Jim

---

