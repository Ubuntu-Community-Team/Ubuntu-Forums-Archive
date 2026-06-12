---
title: "set the user"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by zalnn on 2006-07-11
hi,
i have root access and would like to set the owner of a file to a specific user. how do i do this?
thanks,
--zalnn

---

### Post by digby on 2006-07-11
you use the chown (change owner) command.  It works like this:

sudo chown user.group filename

user is the name of the user who will own the file, and group works the same way.  If you don't know what group to set it to, you can just use the same thing you would for user.

If you're running this on a file that you already own, you don't need to be root to do it.  If you're trying to change someone else's file, you must be root.  Hope that helps!

---

