---
title: "Search Files"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-03-31
How do I search files? Thanks!

---

### Post by Jason_25 on 2006-03-31
Places > Search for Files

in gnome

---

### Post by sn123 on 2006-03-31
[QUOTE=amitroy5]How do I search files? Thanks![/QUOTE]
Open a command terminal and use the find command.
```

$ find directorypath -name "*.txt" -print

```
for more information do
```

$ man find

```

HTH,
S

---

### Post by trent dillman on 2006-03-31
sn123: I believe -name does not allow for metacharacters. I think you meant -iname.

---

### Post by sn123 on 2006-03-31
[QUOTE=trent dillman]sn123: I believe -name does not allow for metacharacters. I think you meant -iname.[/QUOTE]
afair -name does work with metacharacters (?), not on ubuntu to test it out..could somebody verify it for me please?

---

### Post by trent dillman on 2006-03-31
Nope, I was wrong...

jeff@ubuntu:~$ touch file.txt
jeff@ubuntu:~$ find ./ -name *.txt
./file.txt

---

### Post by johnnymac on 2006-03-31
sn is right....wild-cards are accepted for the find command....

---

### Post by professor_chaos on 2006-04-01
using "locate" is even easier. It relys on a database of your files. If you recently added a file, you need to renew the db by "sudo updatedb"

```
locate somefilename
```

---

