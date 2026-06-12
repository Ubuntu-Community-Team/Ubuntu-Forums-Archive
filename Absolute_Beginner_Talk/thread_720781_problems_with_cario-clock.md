---
title: "problems with cario-clock"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2008-03-10
cario clock comes up as a blank white space when compiz is enabeld is there anyway I can stop this from happening?

---

### Post by talsemgeest on 2008-03-10
It may be something to do with the mipmaps

---

### Post by -gabe-noob- on 2008-03-10
mipmaps?

---

### Post by talsemgeest on 2008-03-10
[http://en.wikipedia.org/wiki/Mipmap](http://en.wikipedia.org/wiki/Mipmap)

---

### Post by jordanmthomas on 2008-03-10
I think a long time ago I had this problem and the solution was to make sure the dimensions of the clock weren't powers of two.
128x128 was the default and I'd just make it 127x127 and it would look fine.

Don't know if this is still relevant, but it may be.

---

### Post by -gabe-noob- on 2008-03-13
cool that worked hehe now I have my nice little clock... now how can I make it so it starts up when my computer starts up?

---

### Post by talsemgeest on 2008-03-13
Go to System>Preferences>Sessions and click "ADD".

For the name type Cairo clock (or whatever you want), and for the command type ```
cairo-clock
```

Go "OK" and your done!

Hope this helps :)

---

