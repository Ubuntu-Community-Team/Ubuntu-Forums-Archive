---
title: "Wacom Volito tablet - set up pressure sensitivity?"
date: 2007-10-09
forum: Art &amp; Design
---

### Post by ltk5 on 2007-10-09
I'm trying to set myself up the pressure sensitivity I like. I also did a bit searching
but the results didn't help me much. There was an example of making your brush 
harder but it wasn't enough...

So the problem's that I can't find anywhere on the net (or even on the Linux
Wacom driver homepage) *different presets* for sensitivity of my stylus.
I did, however, find a command for changing this. Just those three numbers
don't make any sense to me. What do they mean?

This are the setting I use atm:
```
xsetwacom set stylus PressCurve 50 0 100 20
```

I'd like to get a bit harder ''stylus'', so I can get the lighter lines easier. When I've 
installed the driver on windows, I just put the slider from *soft* for two steps to the right-*to hard*.

Thanks!

---

### Post by graigsmith on 2007-10-10
[http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)

perhaps this will help.

---

### Post by ltk5 on 2007-10-27
> **graigsmith said:**
> [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)

perhaps this will help.
yup this was about it.

```
  linear curve (default) is "0,0,100,100";
                         slightly depressed curve (firmer) might be "5,0,100,95";
                         slightly raised curve (softer) might be "0,5,95,100".
```

Too bad any more examples aren't posted, but I'll first try with these..

---

