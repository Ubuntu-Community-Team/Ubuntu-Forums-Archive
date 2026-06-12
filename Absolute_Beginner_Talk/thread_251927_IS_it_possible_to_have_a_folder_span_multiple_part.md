---
title: "IS it possible to have a folder span multiple partitions?"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by empcrono on 2006-09-06
Does any one know if it is possible and if so how to do so?

---

### Post by benfindlay on 2006-09-06
Not that I am aware of, however you can have a sub-folder within your folder stored on a different partition/physical drive.

Hope this helps

---

### Post by empcrono on 2006-09-06
ahh i got it then if say usr was getting to big but was to big to move to anthor partion but i still needed room i could move say games within usr to anthor partion and that would work boy i didnt think about that i am going to try it now thank you.

---

### Post by steve.horsley on 2006-09-06
I believe that LVM (Logical Volume Manager) is aimed at creating logical volumes that can span multiple partitions or even multiple drives. You can even add and remove partitions from the volume on the fly as space requirements become apparent. 

I found an intro to LVM last week but can't remember where. Try googling for "linux lvm intro".

---

### Post by empcrono on 2006-09-06
sweet even better

---

