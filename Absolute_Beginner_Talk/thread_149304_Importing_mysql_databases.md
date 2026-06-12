---
title: "Importing mysql databases"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by Nunyah on 2006-03-23
Hey all, where does mysql store its databases? Trying to import from a windows machine..

---

### Post by dvarsam on 2006-03-23
[QUOTE=Nunyah]Hey all, where does mysql store its databases? Trying to import from a windows machine..[/QUOTE]

Hello!

I would be interested too!

I recently was trying to configure a MySQL, PHP & Apache install, while I was learning  how to use MySQL...

I could not make it work, so I formatted my Ubuntu...

_Outcome_:
I have lost ALL my MySQL databases & now I would have to re-type them again...](*,) 

Really, does anybody know what do we have to Backup (or where to put them back in - after a clean install)?

Thanks.

---

### Post by dvarsam on 2006-03-27
I think I have found a solution to our problem:

IF you have installed "mysqladmin", then you can do this:

From the Ubuntu Menu, select "Applications\System Tools\MySQL Administrator"

A window should come up:

1. Under "Server Hostnme", type "localhost"

2. Under "Username", type "root"

3. Under "Password", do NOT type anything, as it is empty.

Click on the button named "connect"

Voilla!!!

You can now work on your MySQL databases...!!!

Not only that, but click on "Backup"....

ONLY after you select it, there will be another name, called "Restore Backup"...

I guess, I have just answered your question now....

Have Fun!!!

P.S.> By the way, I have just found out about this!!!

---

### Post by horace on 2006-03-27
If you use PHPMyAdmin, you can export a database (structure and/or data) and save the output as a text file which contains all the necessary SQL to rebuild it elsewhere.
hth

---

