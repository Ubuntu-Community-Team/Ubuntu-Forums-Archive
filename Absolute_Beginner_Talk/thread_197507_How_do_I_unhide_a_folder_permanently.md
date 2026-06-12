---
title: "How do I unhide a folder permanently?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-15
Hi,

How do I unhide a folder permanently? Is there a toggle hide/unhide?

Thanks.

---

### Post by aysiu on 2006-06-15
Remove the . from the front of the name.

So if you're trying to unhide the Firefox settings folder, for example: ```
mv ~/.mozilla ~/mozilla
``` Of course, if it really is a settings folder, the settings probably won't work any more once you remove the .

---

### Post by racecat on 2006-06-15
Linux doesn't use Windows style attributes for hidden files. It's all in the name. If it starts with a period (.), it's hidden. But as aysiu pinted out, if it's a settings folder (used by a program), the program probably won't work anymore.

Bill

---

### Post by u.b.u.n.t.u on 2006-06-15
Removing the prefix dot did the trick.

Thanks aysiu.

---

