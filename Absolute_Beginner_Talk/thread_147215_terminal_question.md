---
title: "terminal question"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by yellow beard on 2006-03-19
how do you move into a folder with a space in the directory name. eg: Documents and Settings. I know in dos it would be Docume~1 but how do you do it in the linux terminal?

---

### Post by oakz on 2006-03-19
$ cd Documents\ and\ Settings

or

$ cd "Documents and Settings"

---

### Post by engla on 2006-03-19
And learn to use** tab completion**. It's really useful and if you and tab completion get to know each other, you'll be moving blazingly fast in the shell!
So if the only file in a directory is "Documents and Settings", all you have to type is
```
cd Docu<tab>
``` and it will complete to ```
cd Documents\ and\ Settings
```
Super neat. If it was ambigious, say you also had the folder "Documentary" in there, you would be given a list of the matching folders. Then you type some more characters, and type tab again \\:D/

---

