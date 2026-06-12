---
title: "Check Mail in Bitchx"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Lividity on 2007-09-19
Anyone know how to check mail in Bitchx? There's an area next to my nickname that says I have 4 messages.  I've read the man page but I can't figure it out to check the mail.

Here's a picture of what I'm seeing. 

[http://hidebehind.com/BBA0B9]("http://hidebehind.com/BBA0B9")

---

### Post by VeggieMeat on 2008-03-31
I know this is old, but I just happened to come across it and thought someone else might be asking the same question.

The MAIL displayed in BitchX is to let you know that you have new mail for your user on your system.  Usually, this mail consists of system messages.  To check it, open up a terminal and type ```
mail
```

To delete the mail, you can either read it by entering the number next to the message, or typing ```
d 1
``` to delete the message (where "1" corresponds to the message number).  To save what you have deleted, you must exit with ```
quit
```.  EXIT will undelete these messages before it exits.  Give BitchX a little time and it will refresh and not show any new mail.

---

