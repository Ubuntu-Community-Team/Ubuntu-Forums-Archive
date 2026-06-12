---
title: "Reset root path"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by luken8r on 2007-03-23
Is there a way to mimic the root path from / to the working folder? I need to make a build portable and I would like to make my ~/build folder act as /
Is this possible?

---

### Post by Muzik83 on 2007-03-23
If you mean you want to make ~/build your new / (so cd / will take you actually to ~/build) then this is chroot

type 
chroot ~/build

Don't forget you will need basic structures inside build, such as bin with bash inside it if you wish to use the command line

When you're done in the chrooted environment, type exit

-sean

---

### Post by luken8r on 2007-03-23
thanks, I already have that stuff set up, but didnt know how to actually reset the path

---

