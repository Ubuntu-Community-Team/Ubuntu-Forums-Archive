---
title: "how to change owner??"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by NikS on 2008-03-27
I was using windows before shifting to ubuntu..

Now that i have, i cant change the owner of the files n documents i created on my previous os, n so the permissions...

Can anyone please help??

---

### Post by hyper_ch on 2008-03-27
```

chown newUser.newGroup FILE

```

---

### Post by Ub1476 on 2008-03-27
You need sudo priviligies, and as far as I have noticed, usergroup isn't required.

```
sudo chown username nameoffile
```

---

### Post by hyper_ch on 2008-03-27
forgot about the sudo part ^^

group is not required but I do it just to make sure everything ends up the way I want it.

---

### Post by NikS on 2008-03-28
thanks pals..

That should help!!!

:)

---

