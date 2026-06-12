---
title: "loging in"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by kphaueter on 2006-02-15
My son put ubuntu on my laptop and then left for two years to the Ukraine.  I am a Windows user and am absolutely ignorant on Ubuntu. I can log in but need to change the password.  I have no idea how to do it.  Can someone coach me please on how to change the login password?

---

### Post by timbosa on 2006-02-15
You can change your password by going to **System/Administration/Users and Groups** from the menu at the top (if you're using Gnome).

A box will pop up with a list of user names. Select your user name and click on properties. Another box will pop up and you can change your password there.

OR

The more technical way would be to open up a terminal and type
```
passwd
```
Enter your current password, then type your new password twice.

---

### Post by steve.horsley on 2006-02-16
[QUOTE=timbosa]OR

The more technical way would be to open up a terminal and type
```
sudo passwd
```
Enter your current password, then type your new password twice.[/QUOTE]
**No-ooo!!!!** This will set the root password, which is quite undesirable. Just open a terminal window and enter the **passwd** command. You don't need sudo to change your own password.

---

### Post by timbosa on 2006-02-16
Thanks for pointing that out steve. I've edited my post. I guess I'm really not used to the whole sudo thing in Ubuntu yet

---

### Post by kphaueter on 2006-02-18
Merci beaucoup.  That did it

---

