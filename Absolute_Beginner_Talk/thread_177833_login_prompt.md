---
title: "login prompt"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by toppgun on 2006-05-16
ok, this is my first install of linux ever. i installed it on my own without a hitch but when i goes to the login screen i enter the name but when it prompts for the password, i type it but nothing happens, no stars, no text, nothing. i hit enter and it gives me a wierd line that i cant remember. why cant i enter the password i set during install?

---

### Post by bluevoodoo1 on 2006-05-16
[QUOTE=toppgun]when it prompts for the password, i type it but nothing happens, no stars, no text, nothing[/QUOTE]

Are you logging in from a graphical inferface? Or from the command line? If you're entering it from the command line then this is normal. You will not see ### or *** or anything when you're typing your password in a terminal or from ctrl+alt+f1 (command line/console).

---

### Post by toppgun on 2006-05-17
how do i activate the graphics interface?

---

### Post by mostwanted on 2006-05-17
It should have been installed and used by default unless you did a server/minimal install. When you're logged in (it doesn't write stars when you type your password, but it does record it!) type:

```
startx
```

and tell us what happens.

---

### Post by toppgun on 2006-05-17
it says it cannot detect the screen or something like that. could it be the monitor i am using?

---

