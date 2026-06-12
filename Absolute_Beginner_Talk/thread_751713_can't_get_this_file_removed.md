---
title: "can't get this file removed"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by skrap on 2008-04-10
skrap@bill-desktop:~/Desktop$ cd /home/skrap/Desktop/hplip-2.8.4
bash: cd: /home/skrap/Desktop/hplip-2.8.4: Permission denied

how can I get this file off my system

---

### Post by Oldsoldier2003 on 2008-04-10
> **skrap said:**
> skrap@bill-desktop:~/Desktop$ cd /home/skrap/Desktop/hplip-2.8.4
bash: cd: /home/skrap/Desktop/hplip-2.8.4: Permission denied

how can I get this file off my system

```
cd ~/Desktop
sudo rm -r hplip-2.8.4
```

---

### Post by Tatty on 2008-04-10
easiest way is to type ```
gksu nautilus
```

That will open up nautilus (the file manager) with superuser privilages.  Then just browse to the file and delete. 

 Be aware though: you will have access to the entire system from here, so dont delete anything you are unsure of.

**edit:**  Or follow Oldsoldier's command above ;)

---

### Post by haggus on 2008-04-10
if it's a file you can use sudo rm -f <filename> if it's a folder try sudo rm -R <folder>

---

### Post by Oldsoldier2003 on 2008-04-10
> **haggus said:**
> if it's a file you can use sudo rm -f <filename> if it's a folder try sudo rm -R <folder>

rm -r removes files and folders (its always a pretty safe bet wen answering a question when you don't know if its a file or folder the user wants to delete

---

### Post by skrap on 2008-04-11
Thanks so much for the reply They were all right on and the problem is fixed.

---

