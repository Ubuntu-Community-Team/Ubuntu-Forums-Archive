---
title: "Vim going back one character when going up one line"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by J.Vega on 2007-01-17
Hi,
Ic have a little problem writing programs with Vim.
When i write a brackets for functions, I always write both the opening and the closing bracket before filling them with content. So my code looks something like this:
```
function name stuff
{
}
```
Now after writing the closing bracket, I go up one line and press <Enter> to put the stuff into the brackets. I don't know why, but it seems that ViM has changed its behavior about this thing. When I go up a line to the opening bracket, the cursor is set **onto** the bracket it self. So when I press <Enter>, I insert a line before the brackets.
I know it's not a big thing but it's quite annoying to me, so it would be great if anyone could tell me if and if yes how I can change this behaviour. I already looked at the vimrc and the Vim options in the manual, but I found nothing related to this. The only thing I found was the "startofline" option, but this is for PgUp scrolling only.
Also, this doesn't occure when writing text. So it seems to be something related to the brackets.

---

### Post by taurus on 2007-01-17
Maybe you need the vim-full!

```
sudo aptitude update
sudo aptitude install vim-full
```

---

### Post by J.Vega on 2007-01-17
according to the synaptics description of vim and vim-full, the two packages only differ in one thing:
```
This package contains a version of vim compiled with support for
the GNOME2 GUI and scripting support for Perl, Python, Ruby, and
TCL.
```
that is for vim-full
i suppose vim-full is the same as the vim I have, it only has this additional features

or can anyone tell me for sure that vim-full solves this problem?

---

