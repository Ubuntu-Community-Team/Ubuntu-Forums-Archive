---
title: "Partitioning problem"
date: 2008-05-18
forum: Apple Hardware Users
---

### Post by rcx_6000 on 2008-05-18
I have a 80gb macbook pro
i got 56gb for mac os x and 18.2 gb for vista
now i want to install ubuntu by taking 3 gb from vista has i just need it for small stuff i cant do in mac or vista. now the problem i am having is the windows partition is supposed to be last so that bootcamp detects it. i got 3 gb free on the drive now. how do i move the free space so that its between the mac and windows partitions???? i know i can reinstall vista and use diskutil resizevolume but i looking for a way without redoing vista. thanks.

---

### Post by cyberdork33 on 2008-05-18
> **rcx_6000 said:**
> I have a 80gb macbook pro
i got 56gb for mac os x and 18.2 gb for vista
now i want to install ubuntu by taking 3 gb from vista has i just need it for small stuff i cant do in mac or vista. now the problem i am having is the windows partition is supposed to be last so that bootcamp detects it. i got 3 gb free on the drive now. how do i move the free space so that its between the mac and windows partitions???? i know i can reinstall vista and use diskutil resizevolume but i looking for a way without redoing vista. thanks.
i think gparted can move it.

---

### Post by rcx_6000 on 2008-05-18
i thought gparted couldnt move ntfs. if so how???

---

### Post by cyberdork33 on 2008-05-18
> **rcx_6000 said:**
> i thought gparted couldnt move ntfs. if so how???Like I said, "I think". Try it... if it doesn't let you then I was wrong. :)

---

### Post by rcx_6000 on 2008-05-18
do you think it would be easier to just delete vista and redo it in the right order instead of screwing around with the partitions

---

### Post by rcx_6000 on 2008-05-18
if it makes it easier i added you to msn

---

### Post by rcx_6000 on 2008-05-19
nvm its installed and working using grub in the linux ext3 partition with no swap file at all.

---

