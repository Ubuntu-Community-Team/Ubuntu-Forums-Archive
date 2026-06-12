---
title: "HELP!!! How to undelete????"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2008-01-26
I deleted by mistake my home folder from another account I just created with admin rights. I need to restore it but the folder in not in TRASH.  Where can I find it?

What I deleted is the home folder for the other account with limited access rights.

Please help!!!

---

### Post by LaRoza on 2008-01-26
Could it be in the Trash of the account you used to delete it?

Undeleting on ext3 is very difficult...

---

### Post by The Cog on 2008-01-26
It may be in roots trash if you used sudo or gksudo. Use **gksudo nautilus** , use Ctrl-H to show hidden files, then look in **/root/.Trash**.

---

### Post by drowner on 2008-01-26
Exactly right.

If the account you used was root it would be in /root/.Trash

If it was another account you created (say, 'Steve') it would be in /home/Steve/.Trash

And so on...

---

