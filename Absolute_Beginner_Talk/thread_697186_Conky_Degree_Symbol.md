---
title: "Conky Degree Symbol"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2008-02-14
I have a script that runs this:
```
sensors -Af | awk '/+/ {print $1}'
```

And the actual output is:
```
+91°F
```

And I am executing this script with conky, but here is what it looks like on my desktop with conky:
[[img]http://img03.picoodle.com/img/img03/4/2/14/drsmall/f_sensorm_8adc2fc.png[/img]](http://www.picoodle.com/view.php?img=/4/2/14/drsmall/f_sensorm_8adc2fc.png&srv=img03)

How do I fix that??

Dr Small

---

### Post by talsemgeest on 2008-02-15
Sounds a bit pedantic doesn't it?

---

### Post by Bruce M. on 2008-04-06
> **Roland22 said:**
> Try to set "override_utf8_locale no"  to "override_utf8_locale yes"

worked for me.

Gr Roland

> **Dr Small said:**
> Thanks! That was finally the answer to my solution!!
[http://ubuntuforums.org/showthread.php?t=697186](http://ubuntuforums.org/showthread.php?t=697186)

Dr Small

Thought I'd put these here so people reading your thread can see it has been answered with success and you can mark it [Solved].  :)

Conky is almost like "Field of Dreams" with a slight twist:
> 
If you build it, there's more to come!


Have a Great Day, Dr. Small
Bruce

---

