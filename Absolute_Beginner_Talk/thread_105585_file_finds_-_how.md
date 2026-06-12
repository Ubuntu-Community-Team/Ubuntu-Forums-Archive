---
title: "file finds - how?"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2005-12-18
Hey all!

Ubuntu forums and wiki are the places where i ever learned the most about linux. This is a cool network. Anyway, i still a newbie, so here it goes another basic question.

I dload mysql-administrator.  I launch it from the console case its the only way i know.

How can i look for a file locarion?

How can i know where is my mysql-administration?

thx

---

### Post by r4ik on 2005-12-18
Try Synaptic and search for mysql its there.
That is not an answer to our question.(sorry)
Try locations and then search.

---

### Post by Wolki on 2005-12-18
[QUOTE=pedrotuga]
I dload mysql-administrator.  I launch it from the console case its the only way i know.[/quote]

How did you download/install it?

> How can i look for a file locarion?

You men the location of a file? Try "locate <(part of a) filename>".

locate uses a database of the files you have to search quickly, and sometimes this database isn't up to date enough. If that's the case, run "sudo updatedb", this may take some time.

---

### Post by cwaldbieser on 2005-12-18
[QUOTE=pedrotuga]Hey all!

Ubuntu forums and wiki are the places where i ever learned the most about linux. This is a cool network. Anyway, i still a newbie, so here it goes another basic question.

I dload mysql-administrator.  I launch it from the console case its the only way i know.

How can i look for a file locarion?

How can i know where is my mysql-administration?

thx[/QUOTE]

```

$ type mysql-administration
$ which mysql-administration

```
Either of those will find a command on your command PATH.

---

