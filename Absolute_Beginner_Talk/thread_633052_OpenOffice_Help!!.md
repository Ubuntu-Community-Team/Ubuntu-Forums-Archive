---
title: "OpenOffice Help!!"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by JumpmanRugs on 2007-12-06
Ok ive been trying to do some work in openoffice which reuires putting pictures into my Word processing document however everytime i do so openoffice just crashes. Does anybody have any idea why? 

Also, when i try and open OpenOffice Database or OpenOffice Presentation it just comes up with the 'Recovery' screen and opens the word processer in its stead. Again does anybody know why this is?
Any help is much Appreciated =)=) 

Thanks in advance! =)
Peace!

---

### Post by kpkeerthi on 2007-12-06
Launch openoffice from command line and see if you can capture some error information when it crashes

```

soffice -writer

```

As for the recovery screen, OO does it if it crashed last time. As the name indicates, it is a fallback mechanism to recover your unsaved/corrupt document. You can [turn it off]("http://wiki.services.openoffice.org/wiki/Environment_Variables") if you don't wish that option.

---

### Post by JumpmanRugs on 2007-12-06
the Problem with that is it does it almost every time...unless its because most of my files were Microsoft word documents because i only just changed over!

---

