---
title: "Can't understand GNome behavior"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2006-10-14
I have two questions:-

1) My Ubuntu 5.10 is running GNome. When I am in GNome, if I press ctrl+alt+f1, I come back to the login prompt in console mode. When I press ctrl+alt+f7, I find that something appears in console screen and then quickly the GUI appears with the login box. The problem is that I lose my earlier GNome session. I have to login to a fresh GNome session. Can't I preserve this GNome session when I go to tty1, tty2, etc.

2) I am in GNome (ctrl+alt+f7 one). I edit the PATH variable in .bash_profile. I logout and login. When I open a gnome-terminal, the new PATH is not set as per the .bash_profile. The PATH is still the old one. (But when I login to tty1 in the console mode, the new PATH variable is set). What should I do?

Thanks in advance!

---

### Post by CatKiller on 2006-10-14
In answer to your first question, yes you can preserve the session. That is the default behaviour. Something else is killing either your GDM session or your X session. I'm afraid I don't know what that could be.

I don't know anything about your second problem, I'm afraid.

---

