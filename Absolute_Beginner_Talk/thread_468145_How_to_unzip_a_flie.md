---
title: "How to unzip a flie"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-06-08
I've done this before, but can't find where I wrote down the instructions. 

I have a zipped file on my desktop. How do I change the directory to desktop and unzip the file? I realize this is a very basic thing to do, but I can't remember where I wrote those instructions. and can't find them by searching.

Thankis

---

### Post by Cypher on 2007-06-08
What happens when you right-click on this zipped file on your desktop? Is one of the option to open with a archiver or something?

If not, then open a terminal by going to Applications->Accessories->Terminal and type
```

cd ~/Desktop
unzip <filename>

```

---

### Post by Rocket2DMn on 2007-06-08
If the zipped archive is in .tar format, the command is 
```
cd ~/Desktop
tar -xvf filename.tar
```
If it is a tar.gz you need to do this before that tar command:
```
gunzip filename.tar.gz
```

---

### Post by RichPicker on 2007-06-08
Oh yes the tilde (~) that is what I forgot. Sheesh.

Yes, when I right-click it will open with the Archive Manager. But I have never understood what to do with it after that. That sounds stupid, I'm sure. But the Archive Manager is confusing to me. If you'd offer some info on that, I'd appreciate it.

Thanks

---

