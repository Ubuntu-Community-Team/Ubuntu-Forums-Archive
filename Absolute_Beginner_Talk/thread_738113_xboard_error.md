---
title: "xboard error"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by enoughsaid05 on 2008-03-28
hi
I have a XBoard error that says

"Fail to start first chess program gnuchessx on localhost" gnuchessx: no such file or directory"

then the popup appears

" Error to writing first chess program, broken pipe"

What is happening here?

---

### Post by Daveth on 2008-03-28
it would appear from the end of this

[http://ubuntuforums.org/archive/index.php/t-16547.html](http://ubuntuforums.org/archive/index.php/t-16547.html)

that the xboard is a symlink and that the broken pipe is because it is linking to the wrong place, so getting no "feed". But I'm afraid I have no idea to to manually re-point it to the correct directory.

---

