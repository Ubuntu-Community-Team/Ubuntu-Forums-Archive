---
title: "what do I do with .run files?"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Thorndeux on 2006-10-27
Hello people,

I downloaded a file designated as a 'Linux installer'. It has the file extension ".run". Now I don't know what to do with it, really. How do I make it run??

Thanks,
Thorn

---

### Post by almostlinux on 2006-10-27
open up a terminal
cd to directory
give it executable permissions: 'chmod a+x foo.run'
and do a './foo.run'

foo.run being your .run file

---

### Post by wieman01 on 2006-10-27
I think all you need to do is make it executable and then run it:
> sudo chmod +x+x+x [COLOR="Red"]your_file.run[/COLOR]
> [COLOR="Red"]./your_file.run[/COLOR]

---

### Post by matt91 on 2006-10-27
1

---

### Post by Thorndeux on 2006-10-27
Thanks! Seems to work. You people were really quick!

---

