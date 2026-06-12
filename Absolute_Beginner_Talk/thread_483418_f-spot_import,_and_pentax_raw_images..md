---
title: "f-spot import, and pentax raw images."
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by graigsmith on 2007-06-24
i have my default camera import set to f-spot.  so when i stick in my camera card, it pops up and tries to import.  the weird thing is that it ignores all my pentax raw files. *.pef and imports all jpegs. 

it gets weirder, i can use f-spots import button, and go right to the card and it can see and import the pef files and the jpeg files.  

so why can't it just import them right when i stick the card in?


f-spot-import   is the command that gets run whenever i stick my camera card in.  makes me wonder if this is an ubuntu bug, and not a f-spot bug.  mabey ubuntu is just seeing hey, jpegs, they must want to import them, and it doesn't tell f-spot about the pef files. 

anyone have any ideas about this? or mabey a fix?

---

### Post by graigsmith on 2007-06-24
i think i fixed this, i changed my import command from this

```
f-spot-import
```

to this, figured this out on my own, then found the %m thing on the same page that told me to use f-spot-import. which is the old way.

```
f-spot -i %m 
```

---

