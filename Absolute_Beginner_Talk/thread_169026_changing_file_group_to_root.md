---
title: "changing file group to root"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-05-01
How can I change the file group and file owner to root? I need the graphical way and the command for this. 

Thanks

---

### Post by annda on 2006-05-01
```
sudo chown root file_name
```

and

```
sudo chgrp root file_name
```

get more info and options by typing

```
[command_name] --help
```

+ why would you need to do that?

---

### Post by Isoss on 2006-05-01
[QUOTE=annda]```
sudo chown root file_name
```

and

```
sudo chgrp root file_name
```

get more info and options by typing

```
[command_name] --help
```

+ why would you need to do that?[/QUOTE]

Hey, thanks. I found them right after I posted this question. but thanks anyway.

I need them so I can have write permission tp the mysql db files through phpmyadmin. I've been having someproblems with the table not being able to edit any ... now I can do what ever I want with the DB tables.

---

