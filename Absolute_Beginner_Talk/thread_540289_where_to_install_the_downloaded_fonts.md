---
title: "where to install the downloaded fonts"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by arai on 2007-09-01
how to install additional fonts in ubuntu. i downloaded a tgz file (contains fonts). i extracted it to a folder in desktop. now i want to install them. i don't know where to and how to install them.

the fonts are open type ttf fonts.

kindly help me.

---

### Post by Mongo5000 on 2007-09-01
been wondering this myself.  I don't dare try to install them without some advise first.  I installed a new cursor set and screwed something up so i'll wait till someone lends their advise

---

### Post by mcduck on 2007-09-01
If you want to install them for yourself only, ~/.fonts is the right place. For system-wide install put them into /usr/share/fonts.

---

### Post by arai on 2007-09-01
thanks mcduck for the quick reply.

---

### Post by shearn89 on 2007-09-01
but thats not it - you have to copy the fonts into ~/.fonts, and then open a terminal and run
```

sudo fc-cache -f -v

```

to rebuild the font list. Then you can choose them for whatever.

---

### Post by Majorix on 2007-09-01
Try DEFOMA, the DEbian FOnt MAnager. It is in the repos.

---

### Post by shearn89 on 2007-09-01
As a 2nd thought, you can also open nautilus and type font:// (or fonts:// can't remember which) in the address bar, then just drag the font into it.

---

### Post by mcduck on 2007-09-03
> **shearn89 said:**
> but thats not it - you have to copy the fonts into ~/.fonts, and then open a terminal and run
```

sudo fc-cache -f -v

```

to rebuild the font list. Then you can choose them for whatever.

Actually I've never done that but all my fonts work anyway ;)

---

### Post by ramjet_1953 on 2007-09-03
Fonts for system-wide use are installed in /usr/share/fonts

As it is a system directory, I usually just run nautilus in super user mode

[COLOR="Red"]gksu nautilus[/COLOR]

And then create the appropriate sub-directory and copy the new font into it.

Regards,
Roger :cool:

---

### Post by shuttleworthwannabe on 2007-09-03
> **arai said:**
> how to install additional fonts in ubuntu. i downloaded a tgz file (contains fonts). i extracted it to a folder in desktop. now i want to install them. i don't know where to and how to install them.

the fonts are open type ttf fonts.

kindly help me.

where did u get the fonts from? Link?

---

### Post by shearn89 on 2007-09-04
there are some great fonts at [www.dafonts.com](www.dafonts.com)

---

### Post by hyper_ch on 2007-09-04
did you misstype the url? It's not working for me :(

---

### Post by shearn89 on 2007-09-05
yep - my bad, its [www.dafont.com](www.dafont.com)

---

### Post by hyper_ch on 2007-09-05
Thx :)

---

