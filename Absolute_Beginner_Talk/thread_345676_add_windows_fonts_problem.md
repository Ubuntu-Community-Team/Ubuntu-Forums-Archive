---
title: "add windows fonts problem"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by matiz on 2007-01-24
I had just follow a tutorial to type next command in my ubuntu terminal:
find /usr -iname \*.ttf |head -n 5

and the terminal returns:
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/oblique-fonts/LucidaTypewriterBoldOblique.ttf
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/oblique-fonts/LucidaTypewriterOblique.ttf
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/oblique-fonts/LucidaSansDemiOblique.ttf
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/oblique-fonts/LucidaSansOblique.ttf
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/fonts/LucidaTypewriterRegular.ttf

not as the tutorial says:
'/usr/share/fonts/truetype/'

question:
What the above command means?
How to make the system point to right font path? and make my added new fonts displayed correctly?

Thanks for any helper!  :KS

---

### Post by PriceChild on 2007-01-24
I'd advise you to install these packages instead:
```
sudo apt-get install msttcorefonts gsfonts gsfonts-x11
```

---

### Post by matiz on 2007-01-24
thanks, it works well, but tried the command again 'find /usr -iname \*.ttf |head -n 5',
and the system still returns the java**, I just don't know what happened inside the system ??:confused:

---

