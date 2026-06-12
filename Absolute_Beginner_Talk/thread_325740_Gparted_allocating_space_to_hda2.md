---
title: "Gparted allocating space to hda2?"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Paradoxed on 2006-12-26
Good evening all,

Got rid of the NTFS partition and now would like to assign the remaining space to hda2 if possible or any suggestions appreciated. I am a bit confused as to what formatting the remainding space to ext2 will etc etc.

---

### Post by Azakus on 2006-12-26
{EDIT:Misread your question}You can't modify a mounted drive, and since that is your root partition, you'll have to use the LiveCD. When you do it, click on your ext3 partition and click "Resize/Move" on the top of Gparted and resize it to use all of the unallocated space in front of it (Type the numbers, don't just drag the size of the partition because that will miss a few MB's).

---

### Post by Paradoxed on 2006-12-26
Thanks so much. Would it make a difference that I am using an older Ubuntu CD than the current Edgy Eft that I have?

---

### Post by Azakus on 2006-12-26
I don't think so. Both have Gparted Installed.

---

