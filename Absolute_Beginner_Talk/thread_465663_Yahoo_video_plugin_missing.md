---
title: "Yahoo video plugin missing"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-06-05
I am having trouble with watching this [video]("http://www.yahoo.com/s/597718").  I usually can watch videos on yahoo.  The commercial works but then I get this error:

> Unknown Plugin (application/x-ms-wmp)

Any ideas on what I need?

---

### Post by tdrusk on 2007-06-05
I think it's missing Windows Media  Player. 

This should work...
```
sudo aptitude install mozilla-plugin-vlc
```

EDIT: This doesn't work. i guess just wait for more replies. Sorry I can't help. I'm going to bed.

---

### Post by wormser on 2007-06-05
> **fuzzyhair said:**
> I think it's missing Windows Media  Player. 

This should work...
```
sudo aptitude install mozilla-plugin-vlc
```

EDIT: This doesn't work. i guess just wait for more replies. Sorry I can't help. I'm going to bed.

Yeah, I just tried it and it does not work.

---

### Post by wormser on 2007-06-06
Can anybody watch this video on [yahoo]("http://www.yahoo.com/s/597718")?

---

### Post by buckwheat12n on 2007-06-08
FWIW, I'm having the exact same problem when attempting to watch videos on Yahoo.  I can view the commercial but then get that I'm missing a plugin even though I do have w32codec's installed.

---

### Post by fumduck on 2007-06-08
i am having the same exact issue also

---

### Post by wormser on 2007-06-09
It appears that M$ has a new format and linux is not set up for it yet.  I also have the same issue with abc.com.  I think they are 2 new codecs.

The error is Unkown Plugin (application/x-ms-wmp)

When I search the web I only find a couple of links and not much information.  Does anybody have more insight to this issue?

---

### Post by cabko on 2007-06-09
i had same problem...i solve it by automatix...u can inslall it from repositories...than just let it install all codecs...maybe this will help

---

