---
title: "Parental Controls and Restricted Computer Access"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by eoghanmurray on 2007-06-17
I was wondering whether there are any programs that both restrict web access and prevent local things like changing the desktop background, changing homepage, theme, password etc...
Even if it's a bunch of separate programs, I don't mind.

Thanks for any help! ;)

---

### Post by KIAaze on 2007-06-19
A)Restrict Web Access: [DansGuardian]("http://dansguardian.org/")

B)prevent local things like changing the desktop background, changing homepage, theme, password etc...:
*[Locking Mozilla Firefox Settings]("http://ilias.ca/blog/2005/03/locking-mozilla-firefox-settings/")
*To prevent the user from changing the rest, I think the simplest thing to do would be to change the permissions of the commands/programs/files used so that the user can't use/access them.

Unfortunately, I don't know exactly which files/commands are used to change the background and theme.

For the password, the command to change it is "passwd", so to block it, all you need to do is this:
```
sudo chmod 744 /usr/bin/passwd
```

(I can't verify if it's in /usr/bin since I'm currently under Windows, but you could type ```
which passwd
``` to find out or ```
whereis passwd
``` to get all possibilities.)

P.S: You could also have a look at the programs used in Ubuntu Christian Edition since it comes with parental controls as far as I know. (at least with dansGuardian)

---

