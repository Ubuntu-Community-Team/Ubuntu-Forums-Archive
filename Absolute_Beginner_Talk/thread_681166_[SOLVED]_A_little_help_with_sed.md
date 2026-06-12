---
title: "[SOLVED] A little help with sed"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2008-01-28
I'm writing a script and need a little help with sed.

Currently, here is what I need to do.
I need to delete every line that begins with "DesktopBackgroundImage" with sed, somehow. Currently I have:
```
sed '/^DesktopBackgroundImage / d' preferences
```

But it isn't deleting those lines from preferences.

Any ideas how to do this? I've been reading here for ages, but can't seem to get it to work properly:
[http://www.grymoire.com/Unix/Sed.html#uh-30](http://www.grymoire.com/Unix/Sed.html#uh-30)

Dr Small

---

### Post by jpeddicord on 2008-01-28
> **Dr Small said:**
> I'm writing a script and need a little help with sed.

Currently, here is what I need to do.
I need to delete every line that begins with "DesktopBackgroundImage" with sed, somehow. Currently I have:
```
sed '/^DesktopBackgroundImage / d' preferences
```But it isn't deleting those lines from preferences.

Any ideas how to do this? I've been reading here for ages, but can't seem to get it to work properly:
[http://www.grymoire.com/Unix/Sed.html#uh-30](http://www.grymoire.com/Unix/Sed.html#uh-30)

Dr SmallStab in the dark:
```
sed '/^DesktopBackgroundImage.*$//' preferences
```

---

### Post by spiderbatdad on 2008-01-28
so why the spaces between DesktopBackgroundImage / d' ?

---

### Post by Dr Small on 2008-01-28
Thanks for the help guys.
I finally got it figured out.

```
cat preferences | sed '/^DesktopBackgroundImage.*/d' > preferences
```

I had to remove that one line, yet keep the rest of the file, whereas before and on different attempts, it was completely erasing the file.

So, this thread is Solved :)
Thanks again!

Dr Small

---

### Post by apostate on 2008-01-29
I was going to say, sed doesn't actually do *anything* to the source file, it only does what you ask to the output. So, you have to redirect to a new file to save it that way, hence the > filename.txt

---

