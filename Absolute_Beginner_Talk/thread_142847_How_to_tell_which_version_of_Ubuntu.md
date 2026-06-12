---
title: "How to tell which version of Ubuntu"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by minghai on 2006-03-11
Hi,

   How do I tell which version of Ubuntu I have installed (Hoary, Breezy, Warty)?  Is there a command I can issue on a command line?  Thank you.

Ming Hai

---

### Post by Xian on 2006-03-11
$ cat /etc/issue

---

### Post by minghai on 2006-03-11
Thanks!

---

### Post by kayas80 on 2006-03-11
[quote=Xian]$ cat /etc/issue[/quote]

Done that and it says I am using Ubuntu 5.10 "Breezy Badger" \n \l

Just wondering what the \n\l mean?

---

### Post by engla on 2006-03-11
[QUOTE=kayas80]Done that and it says I am using Ubuntu 5.10 "Breezy Badger" \n \l

Just wondering what the \n\l mean?[/QUOTE]
The /etc/issue file contains the welcoming text that is displayed in the ttys [accessed by typing ctrl-alt-F1 to F6, get back to X with ctrl-alt F7]

according to 'man getty', \n is replaced by the computer's name, and \l is the name of the tty (eg. tty2)

---

