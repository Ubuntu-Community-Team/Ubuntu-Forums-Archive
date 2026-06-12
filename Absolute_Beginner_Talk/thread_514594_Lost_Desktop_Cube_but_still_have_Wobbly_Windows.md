---
title: "Lost Desktop Cube but still have Wobbly Windows?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by bertlacy on 2007-07-31
Hey guys,

I don't know what happened but all of the sudden i don't have the cube effect anymore?  I am not using Beryl, just the desktop effects for ubuntu.  

I have changed the number of desktops to 4 but it still doesn't work.

---

### Post by pacsum on 2007-07-31
yes I have the same problem. BTW nice avatar :lolflag:

---

### Post by bertlacy on 2007-07-31
HAHA, Thanks, I think that it shows my best side!

---

### Post by yorkie on 2007-07-31
COMPIZ CUBE  If you want to get the cube to work do the following  open terminal type these  commands 

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

---

### Post by bertlacy on 2007-07-31
That Got It!!!!

Thank You!

---

