---
title: "Guest account no sound [Resolved]"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Bobtheknight on 2006-12-03
Dear forum goers,

I have a problem for you guys.  I have a main account with admin priviledges and sound was working here.  I made a guest account and sound doesn't work there.  The speaker icon on the top right of Ubuntu has a cross on it.

Now how would I fix that?

Thanks in advance

---

### Post by CatKiller on 2006-12-03
It might not be the problem, but I believe that "use audio devices" is a privilege you can give or take away from a particular user. It might be worth checking that in the Users and Groups tool.

---

### Post by IYY on 2006-12-03
I'm sorry that I can only give you this command-line solution. It's the way I would go about fixing it, even though I know there must be a graphical way to do it:

You need to edit the file /etc/group and add your guest account to the list of users on the line where the first word is 'audio'.

---

### Post by Bobtheknight on 2006-12-04
Wow that worked.  I can't believe that happened, it's so simple.  So I guess when I create a user with adduser on command line it doesn't come with any priviledges huh.

---

