---
title: "Reading ALL Terminal Output"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2007-04-10
I installed TREE to check my directories. It works perfectly and I can see the output in the Terminal as it occurs, but when I attempt to scroll back to the beginning I can only view part of the output.
  Is Terminal output limited to the last couple of hundred lines? Is there a way to scroll back to the beginning of the TREE output in the Terminal?
Thanks

---

### Post by zvacet on 2007-04-10
```
tree -a
``` 

other commands you can find in** man tree**

---

### Post by steve.horsley on 2007-04-10
My choice would be either to direct the output to a file (which you can then view with gedit):
**tree > tree.txt**
or pipe it through less, which allows full scrolling:
**tree | less**

---

### Post by Stunt Double on 2007-04-10
Thanks for the help.

---

### Post by devnulljp on 2007-04-11
pipe it to less or more

tree | less
tree | more

---

