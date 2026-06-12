---
title: "Finding C and D disk"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Neur0123 on 2007-05-09
Hi
I have recently installed Ubuntu, and i noticed i cant find my harddisks anywhere, becouse i have all the stuff i need there it would be nice if someone could tell me what to do.

Thank you
Neur0123

---

### Post by Stickymaddness on 2007-05-09
Can you not see them in Places->Computer?

If not, open a new terminal and type:

```

sudo fdisk -l
cat /etc/fstab

```

The password it will ask you for is the same as your login password. Try that, and then paste the output here.

---

### Post by Neur0123 on 2007-05-10
Yes that worked, thank you for the fast reply:) 

Neur0123

---

### Post by drowner on 2007-05-10
> **Neur0123 said:**
> Yes that worked, thank you for the fast reply:) 

Neur0123

That didn't work.

The commands were to

1. List the drives ubuntu can see

2. List the places ubuntu has them mounted, for you to access them...

None of those commands actually made it MOUNT them, so i put it to you, it was fixed before you started!

---

### Post by Najand on 2007-05-10
Hmm, maybe he just found the partitions he were looking for.

---

