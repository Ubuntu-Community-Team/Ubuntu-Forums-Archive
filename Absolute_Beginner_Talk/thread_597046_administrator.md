---
title: "administrator"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by rickconroy on 2007-10-30
Hi Ubuntu users,
I was the Administrator before I tried to upgrade to 7.10. Now I can't do anything! I get messages that tell me that I have to ask the Administrator even when I use the sudo command! I have another message on the usual update icon saying "This usually means that your installed packages have unmet dependencies". But it won't let me do anything about it.
HELP PLEASE

---

### Post by taurus on 2007-10-30
Do you belong to both adm and admin groups in /etc/group?

```
id
```
You don't happen to modify /etc/sudoers at all, do you?

---

### Post by rickconroy on 2007-10-30
I'm not sure? I use to just sign in and give my password when I needed to update etc. I did try to Identify myself in "users and groups" and that seems to have made the problem worse, because I can't get back in there. I downloaded Gutsy Gibbon for several hours and that was the situation when I returned. I did try to Identify myself in "users and groups" and that seems to have made the problem worse, because I can't get back in there.
Cheers.

---

### Post by rickconroy on 2007-10-30
It doesn't accept my password. If I type in "su" in terminal and give my password. It comes back with ":su Authentication failure Sorry."

---

### Post by Dr Small on 2007-10-30
Try:
```
sudo su
```

---

### Post by rickconroy on 2007-10-30
Maybe I should start from scratch, or go back to the Bill Gates system!

---

### Post by Austin_KW on 2007-10-30
I think you need to add yourself to the admin group.

If you do not have a privileged user then you need to boot single user (recovery mode) from the grub menu. This will give you a terminal interface as the root user where you have all privileges and can do anything

Once you get to the single user mode add yourself to the admin group
```
 usermod -a -G admin ***yourUserName***
```

Then continue booting up to multiuser mode (2) wherw you should have admin privs ```
telinit 2 
```

---

### Post by rickconroy on 2007-10-31
Thanks I tried usermod. I should have stayed with Feisty Fawn. At least I had no problems.
Thanks to everyone, But I think I'll just give up!

---

