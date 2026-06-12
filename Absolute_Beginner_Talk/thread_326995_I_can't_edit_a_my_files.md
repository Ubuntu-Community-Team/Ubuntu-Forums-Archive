---
title: "I can't edit a my files"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by cap10kirk on 2006-12-28
when i go to Applications => Accessories => text editor, and try to edit the my.cnf file, I get an error message: you do not have the necessary permissions to save the file.

soooo, how do I get the necessary permissions?:confused: 

thanks for your noob patients:KS

---

### Post by meng on 2006-12-28
This file probably does not have write permissions for ordinary users, only for root. Best is to go to terminal:
gksu gedit /etc/my.cnf
(I assume that's where your file is)

---

### Post by teet on 2006-12-28
Hit Alt + F2

Then type "gksudo gedit" without the quotes.

Enter your root password in.

Then open the file from gedit and make the changes you want to make.

-teet

---

### Post by cap10kirk on 2006-12-28
thanks guys. that did it.

Kirk

---

