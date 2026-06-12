---
title: "Gnome3 suddenly Oh no!"
date: 2013-02-14
forum: Any Other OS
---

### Post by waldherrvonbirnbaum on 2013-02-14
Hallo, yesterday i did an update of Wheezy Debian on my Samsung Netbook. Later I installed a bunch of packages on it. Over night i put it to hibernate and today morning I restarted my computer. The greeting after login was

[I]"Oh no! Something has gone wrong.
A problem has occurred and the system can’t recover.
Please log out and try again.
[Log out]".
[/I]
I dont know from where it comes.

My fix is quick and dirty, but it works (in Ubuntu too):
Log into terminal (Ctrl+ALT+F1) as root and add a new user.

```
# adduser userx
```Now i answered what was asked. Ctrl+ALT+F7 brang me back to GUI and i logged in as userx.
Now I changed back to the Ctrl+ALT+F1 terminal and removed the /home/yourUserName/.config folder.
```
# rm -R /home/yourUserName/.config
```The next step is to copy the .config folder from the new userx account to your normal user account folder.
```
# cp -R /home/userx/.config /home/yourUserName/ 
```now press Ctrl+ALT+F7 to check, if it worked.

If it is good now, delete the new userx ```
# userdel -r userx 
```**NOTE!!!**
all your settings will be gone, but at least it is working again.

---

### Post by howefield on 2013-02-14
Thread moved to the "*Other OS/Distro Talk*" forum.

---

### Post by MadmanRB on 2013-02-14
Yeah no wonder why debian is moving away from gnome 3 and using XFCE

---

### Post by jwbrase on 2013-02-14
Just be aware that this fix will reset the configuration for a large number of programs. This includes the saves and high scores for a number of games. (Don't worry, I didn't find this out the hard way: I just looked at what's stored in my .config directory on a smoothly running system).

---

