---
title: "Error message"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2007-10-09
Have only been using Ubuntu, Feisty Fawn for a few days now but i am convinced that in my humble opinion it is much better than Windows. The only problem is when the computer boots-up and before i am required to enter my name and password an error message appears which states:
 
Analog RGB
640 x 350 82Hz
Out of range

Could someone explain what's happening here and how i might resolve it!
Big thanks

---

### Post by philinux on 2007-10-09
This is to do with the graphics adapter and how it was recognised or not during the install. If you wait 9 days for gutsy version 7.1 and can put up with the error for now, gutsy has a gui for sorting this out.

If you cant wait you'll have to reconfigure your xorg with

```
sudo dpkg-reconfigure xserver-xorg 
```
from the terminal.

---

### Post by oscarthefish on 2007-10-09
Hiya Philinux, can wait for 9 days and Gutsy version 7.1 no prob. Thanks for the reply mate

---

