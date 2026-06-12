---
title: "Deleting A Folder"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by magnoliablossom on 2006-08-19
How do you delete a folder that is write only or something or other....I tried:

> rm ~/Downloads/jdk1.5.0_07 -r 

but it just makes me go through every single file (and man there are a lot of 'em!) pressing "y" then entire and then telling me access denied or something or other.

---

### Post by melissawm on 2006-08-19
```
rm -rf folder/
```

But be careful, that does delete everything without asking any questions or confirmations.

---

### Post by magnoliablossom on 2006-08-19
thanks....i tried that and got a screen full of:

> rm: cannot remove `/home/heaven/Downloads/jdk1.5.0_07/man/ja_JP.eucJP/man1/serialver.1': Permission denied
rm: cannot remove `/home/heaven/Downloads/jdk1.5.0_07/man/ja_JP.eucJP/man1/idlj.1': Permission denied


and so on :(

---

### Post by bulldog on 2006-08-19
Use the sudo command,but be sure you don't need the folder anymore!

sudo rm -rf

---

### Post by magnoliablossom on 2006-08-19
YES!  TY TY TY TY TY TY TY TY!!!!!....That folder in my downloads folder was bugging the life outta me! lol  And no, I don't need it anymore.  TY!  TY!  TY!!!!!

---

