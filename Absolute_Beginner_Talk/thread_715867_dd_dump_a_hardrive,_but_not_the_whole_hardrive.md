---
title: "dd dump a hardrive, but not the whole hardrive"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by paxmanchris on 2008-03-05
i have a hardrive that has about 1gb information. but it is a 80gb hardrive.

what dd command would i use to only dump what is necessary.

note: i want to dump it to a iso. that i will later use to clone the drive to other drives.

---

### Post by ruy_lopez on 2008-03-05
You can only use dd on entire partitions and disks.

---

### Post by paxmanchris on 2008-03-05
is there nothing i can do?

i suppose i could just us the 'cp' command.

what i am going to do is install ubuntu on to one drive, and then clone it to other drive, so i do not have to go through the install process again.

any tips?

---

### Post by ruy_lopez on 2008-03-05
If the drive is identical in size, you can use dd to clone it. I've never tried it myself.

The problem you face is that different systems will need different installations. You can't just take a drive out of one system and place it in another, unless it has identical hardware.

---

