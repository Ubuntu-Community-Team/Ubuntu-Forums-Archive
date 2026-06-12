---
title: "ubuntu font"
date: 2013-05-26
forum: Art &amp; Design
---

### Post by ZootHornRollo on 2013-05-26
Hi,

can anyone explain why the Ubuntu font, when using Gimp at least, flits between a round lower case 'a' and curly one depending on whether it is in italics or not?

---

### Post by Newfoundlander on 2013-05-28
Many fonts have a separate italic version (known as true italic) with certain letters having special shapes (most noticeably the a and f).  If you were to disable or delete the italic version of Ubuntu and restart GIMP then you would see what is known as a fake italic -- the same typeface simply slanted to the right.

---

### Post by ZootHornRollo on 2013-06-01
thank you.

any way to get the 'italic' version upright?

---

### Post by ofnuts on 2013-06-01
- Create text layer with italic font
- Layer->Text to path
- Use the shear tool to apply the transform to the path to make the italics upright
- Select from path, bucket fill or else:

[IMG]http://i.imgur.com/qeQdYYO.png[/IMG]

---

