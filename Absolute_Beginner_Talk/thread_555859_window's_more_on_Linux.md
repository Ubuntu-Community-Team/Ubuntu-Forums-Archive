---
title: "window's more on Linux"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-09-20
In windows, there is a command called "more" that, given a string of input, it returns the first 27 lines (the size of the screen), pauses and then shows the latter 27 until the string is over. Is there an equivalent to this on Linux?

---

### Post by 505 on 2007-09-20
Have you tried the command 'more'?? You can also try the command 'less' which lets you scroll a text per line, where you can also scroll back.

---

### Post by energiya on 2007-09-20
more <file>
and for line-by-line
less <file>

[505 was faster]

---

### Post by Lord Illidan on 2007-09-20
For example, given this command dmesg, it will fill in the screen and you'd need the scrollbar to see all the content.

However, in Linux, you can use dmesg | more or dmesg | less to read it in "stages".

The | is called a pipe, to pipe the output of one command into another.

---

### Post by Bothered on 2007-09-20
As said above, there's command in linux also called "more" that does that, e.g. more [file]. Personally I prefer "less", it has more features (ironically).

---

### Post by RedSquirrel on 2007-09-20
> **Fixman said:**
> In windows, there is a command called "more" that, given a string of input, it returns the first 27 lines (the size of the screen), pauses and then shows the latter 27 until the string is over. Is there an equivalent to this on Linux?
You can also try looking up a command in the manual pages to see if it exists. For example:

```
man more
```

If there's a manual page, well, then there is such a command. ;)

You also type "mo" and hit the TAB key twice to see what commands start with those letters.

As noted above, some people prefer **less** (even the man page for 'more' claims that *less* is more). :)

---

### Post by energiya on 2007-09-21
Forgot about "most". Very nice when using man (it has pretty colors :D )

---

