---
title: "cheese messes up screen"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-03-03
So i just downloaded and installed Cheese. It is supposed to be a linux version of the Apple Photo Booth.

Anyway I tried it out and when I took the picture it screwed up my display. Everything went bright and washed out, almost like the Gamma on my display got maxed out...

I had to logout and login again to fix the problem.  

Anybody have any clue on how to fix this?

Or does anybody know of any good software for using the a built in camera?

---

### Post by Zaphod on 2008-03-03
I think Compiz+cheese can cause trouble . At least it worked that way for friend of mine , just turned off Compiz then Cheese worked..

---

### Post by Technoviking on 2008-03-03
Did you install the cheese package from the repo, or built by hand? The white screen I think is usually a xorg driver problem, what type of video card do you have and are you using compiz or beryl?

Mike

---

### Post by neurostu on 2008-03-03
I installed cheese with:
```

sudo apt-get install cheese

```

I have an nvidia video card, it came built into my t61. I think its a nvidia quadra 140m

I am also using compiz

---

### Post by neurostu on 2008-03-04
So it was compiz. I turned off desktop effects (and aside from crashing FF) cheese worked.

---

