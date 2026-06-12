---
title: "Problem with line 8"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Mrpelletier on 2006-11-11
Ok here is my problem. Every time i go to install stuff For example in this case i am trying to install kiba dock There is something that sais "E: Type 'Uncomment' is not known on line 8 in source list /etc/apt/sources.list"
This is very wierd. Can someone help me on this?

---

### Post by woedend on 2006-11-11
open a terminal.
type gksudo gedit /etc/apt/sources.list

if on kde, i think it would be kdesu kate   instead of gksudo gedit above.

go down to the eighth line, and put a # in front of the word uncomment and save.

---

