---
title: "[SOLVED] Remove a user?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by SDL on 2007-11-10
I've created an extra user profile that I don't really want. Is there any way to completely remove the user please?

If I use System->Administration->Users_and_groups to remove the user, I cannot delete the users home folder.

Many thanks,

Stephen.

---

### Post by robc02 on 2007-11-10
You can manually remove the user's home directory in Nautilus as Sudo (sudo nautilus).

You can also do it in command line - I think this is it, but I normally use nautilus so can't be certain:

sudo rm /home/user_name

---

### Post by anaconda on 2007-11-10
No I think it is:
sudo rm -R /home/user_name

But doing it with nautilus is safer

---

### Post by SDL on 2007-11-10
Thanks very much. I ran Nautilus and it worked perfectly.

---

