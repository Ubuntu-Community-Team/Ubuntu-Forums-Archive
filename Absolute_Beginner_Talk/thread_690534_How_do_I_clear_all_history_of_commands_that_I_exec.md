---
title: "How do I clear all history of commands that I executed?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-02-07
Hi
thank you for reading my post
I use tcsh and normal gnome-terminal, can you tell me how I can delete history of tcsh and gnome-terminal commands?

Thanks

---

### Post by deepclutch on 2008-02-07
run "history -c".

---

### Post by jw5801 on 2008-02-07
Or you could use:
```
echo "" > ~/.bash_history
```
Then after you close the terminal and open it again you'll only have that command in your history. That's pretty much a hack though, I'm sure there's a more graceful way to do it!

---

### Post by scorp123 on 2008-02-07
> **jw5801 said:**
>  Or you could use:
```
echo "" > ~/.bash_history
```  You did read his posting, yes? He uses **[COLOR="Red"]tcsh[/COLOR]** ... not **[COLOR="Blue"]bash[/COLOR]** ... I am sure "tcsh" uses a different config file and not bash's files.

> **jw5801 said:**
>  That's pretty much a hack though, I'm sure there's a more graceful way to do it  This command:
**history -c**

---

### Post by jw5801 on 2008-02-07
Whoops! Missed that :$

My apologies!

---

