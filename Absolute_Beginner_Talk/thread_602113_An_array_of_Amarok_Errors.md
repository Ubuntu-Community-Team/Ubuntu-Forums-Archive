---
title: "An array of Amarok Errors"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by It_Was_Luck on 2007-11-03
Well someone told me to get Amarok so I went and got it and I ran it and I got all these errors.

[[IMG]http://img220.imageshack.us/img220/904/amaroksh8.th.png[/IMG]](http://img220.imageshack.us/my.php?image=amaroksh8.png)

Luckily me being smart (I was for awhile) I logged in as a root in the terminal than ran it and it ran perfectly. But once I exit my terminal or just try to open Amarok normally all those errors appear again.

How can I make it so that it always opens up as root? Or in other words how can I fix this?

---

### Post by FuturePilot on 2007-11-03
It looks like possibly a permission problem. Delete your .kde folder. It's hidden so press Ctrl+H to unhide it. Then try running it again. Not as root though.
It's best not to run it as root. That could have possibly created the permission problems in the first place.

---

### Post by It_Was_Luck on 2007-11-03
Okay so where is this .kde folder? and is it really safe to remove it?

EDIT: actually i found the folder but all there is in it is a folder called Autostart and env, the qutostart one has some beryl text which i dont know why cause I dont even have beryl, and the other one is empty

---

### Post by FuturePilot on 2007-11-03
Yes, it's safe to remove it. It only holds your config files for KDE applications. If you want you could also just rename it something else like .kde_old for now.

---

### Post by It_Was_Luck on 2007-11-03
I can't remove it, it has a little lock symbol next to it and when i try to delete it it says cannot move to trash, then because i dont have premission

edit: i renamed the folder to .kde_old and it appears to be working...

---

### Post by FuturePilot on 2007-11-03
Ok, try this
```
sudo chown $user -R .kde
```
where $user is your user name

---

