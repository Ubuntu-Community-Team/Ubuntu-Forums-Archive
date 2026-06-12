---
title: "Hibernation Fails"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-09-29
My Linux wont Hibernate :(
My Windows Will though, so its defo a Linux problem :(

Any ideas?

---

### Post by po0f on 2006-09-29
Captain Kirk76,

You will have to look into the ACPI support your motherboard has under Linux.

---

### Post by Captain Kirk76 on 2006-09-29
ooOO thats sounds a little over my head!

---

### Post by Daniel15 on 2006-10-08
Make sure that your swap partition is big enough. When you hibernate, the entire contents of your RAM is saved to your swap partition. Hence, the swap partition needs to be fairly large.

On my laptop with 1 GB of RAM, I made the swap partition 1.5 GB. This works fine for me :)

---

