---
title: "can´t dlete trash"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by peterpan1 on 2006-06-10
opening my trash and telleing him to empty i get the message i´m unable, cause i do not have the rights to write on parentfolder

---

### Post by userundefine on 2006-06-10
Strange.  Can you delete from terminal? Open a terminal, then type
```
cd ~
cd .Trash
rm -i *a filename*
```
What happens if you do that?

---

### Post by peterpan1 on 2006-06-10
hi it deletes, but it are to many files and folders and i found on google the command: rm -fr $HOME/.Trash/
did that. it worked out
but thanx for your help

---

### Post by userundefine on 2006-06-10
Yeah, I was going to tell you to do that next, but you don't want to send someone into the terminal with **rm -rf** without some caution. :)

---

