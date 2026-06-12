---
title: "anyone know a terminal that does not display uer names?"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-10-03
im looking for a terminal like the mac terminal. that hides uer names and doesnot have any facy borders or anything.

thanks

---

### Post by bswilson on 2006-10-03
> **jinxjinx said:**
> im looking for a terminal like the mac terminal. that hides uer names and doesnot have any facy borders or anything.

You can modify your prompt to be anything you want.  Edit your .bashrc file in your home directory, and find where it assigns a variable to PS1 and to PROMPT_COMMAND.  Change them to be whatever.

---

### Post by bodhi.zazen on 2006-10-03
> **jinxjinx said:**
> im looking for a terminal like the mac terminal. that hides uer names and doesnot have any facy borders or anything.

thanks

You can configure most terminals the way you like. With gnome-terminal edit your profile.

To customize the bash prompt:

```
gedit ~/.bashrc
``` and edit away. See this link:

[How to Bash prompt](http://www.linuxjournal.com/article/3215)

---

