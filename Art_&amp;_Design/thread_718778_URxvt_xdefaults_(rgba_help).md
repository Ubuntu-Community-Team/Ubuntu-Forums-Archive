---
title: "URxvt xdefaults (rgba help)"
date: 2008-03-08
forum: Art &amp; Design
---

### Post by PurposeOfReason on 2008-03-08
Typical rgb output is three numbers, three times. In Xdefaults it is four numbers long, so it is like 0000/0000/0000. Why is this and where does the fourth number come from?

---

### Post by mrsteveman1 on 2008-03-08
RGB is usually 3 8-bit numbers right?

Whats an example of these 4 digit numbers you are seeing?

---

### Post by kerry_s on 2008-03-08
you can use standard names to.
example:
URxvt*background: black
URxvt*foreground: white

---

### Post by PurposeOfReason on 2008-03-08
> **mrsteveman1 said:**
> RGB is usually 3 8-bit numbers right?

Whats an example of these 4 digit numbers you are seeing?

urxvt.background:  rgba:7860/6830/5600/eeee
urxvt.foreground: rgba:3860/3030/2500/ffff

> **kerry_s said:**
> you can use standard names to.
example:
URxvt*background: black
URxvt*foreground: white

THen you can't use an alpha channel.

---

### Post by kerry_s on 2008-03-09
> **PurposeOfReason said:**
> 
THen you can't use an alpha channel.

my bag, alpha channel thats for composite?

it's not for transparency, cause i don't use that but i do have transparency.

---

### Post by PurposeOfReason on 2008-03-09
> **kerry_s said:**
> my bag, alpha channel thats for composite?

it's not for transparency, cause i don't use that but i do have transparency.
You probably use inherit pixmap? The alpha channel, when used with composition, gives you real transparency. Anyways, I found out you can just put something like [90]#000000 for 90% 10% transparent.

---

