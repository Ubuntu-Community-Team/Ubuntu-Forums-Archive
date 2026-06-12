---
title: "slax and .run files"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by overownt on 2007-07-31
i installed slax and was looking to install some linux game demos but me being a noob didnt  know how to run the files labeled .run 

when i click it to run it, it opens in a word document. i am looking to install quake 3 and quake 4, both demos for linux. both labeled with the type .run

---

### Post by KIAaze on 2007-07-31
Right-click->Properties->Permissions
check the "make executable" box

double-click on the .run file and select "run" or "run in terminal"
(in terminal is better so you can see error messages if there are any)

Or the command-line way:
```
chmod +x file.run
./file.run

```

---

### Post by overownt on 2007-07-31
thanx ill try it

---

### Post by overownt on 2007-07-31
umm
it gets ready to run but then the terminal never opens

---

### Post by KIAaze on 2007-07-31
Try to run it directly from the terminal:
```
cd <directory where the file is>
./file.run
```

---

### Post by hammad1337 on 2007-07-31
try: ```
sh file.run
``` in terminal

---

### Post by overownt on 2007-07-31
thanks alot :D

---

