---
title: "Is it possible to create file from Terminal?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by royksol on 2007-05-04
I want to write script using Zenity. And when user enter some data I want to save it into a file. Can I do it with some bash commands or not?

---

### Post by Bachstelze on 2007-05-04
Just edit the file as if it were there. If it does not exist, your editor will create it.  If you just want to create an empty file, you can use *touch*, for example :

```
sudo touch /path/to/file
```

---

### Post by compmodder26 on 2007-05-04
Never used Zenity before but run the command you would normally use and then append "> /path/to/file" on the end of it, e.g.:

```
your_zenity_command > /path/to/output/file
```

This will redirect all output from your command to the file you specify

---

### Post by royksol on 2007-05-04
**compmodder26** It works. But when file exists it rewrites the file. It would be great if there is a way to append or write to file a bit more than result of command

---

### Post by compmodder26 on 2007-05-04
Okay, change ">" to ">>".  That will append.

---

