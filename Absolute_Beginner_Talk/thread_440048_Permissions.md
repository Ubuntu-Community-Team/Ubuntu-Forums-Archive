---
title: "Permissions"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by WElliott on 2007-05-11
Newbie to Linux - trying to learn about file systems and rights, etc.

How do I give a user permissions to a directory? For example... download a new theme and I want to extract and place it in the themes directory however I am told that my user does not have rights to do so. How would I change the rights on the directory to allow this? The user I created is a member of the root group already...

Thanks for your help!

---

### Post by taurus on 2007-05-11
If you need to write to anywhere outside your $HOME directory, you need to use the sudo in front of the command from a terminal.  Otherwise, press <Alt>F2 and type

```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by WElliott on 2007-05-11
Thanks so much!! Got it now.

---

### Post by mcduck on 2007-05-11
Do not *ever* change permissions of system directories, it might, in many cases, break your system beyond repair.

Instead change your own permissions, by using 'sudo' to temporary gain root privileges: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

In this case, hit Alt-F2 and run 'gksudo nautilus' to open the file manager with root privileges. Then you can use that to drop the theme files into correct directory.

---

