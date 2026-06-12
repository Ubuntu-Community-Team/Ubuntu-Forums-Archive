---
title: "Command to &quot;take out the trash&quot;?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Redeyes_Gambit on 2007-03-09
}{i,

Lol, one silly little question:

What is the command to empty the trash? 

I must have thrown something away that requires sudo privileges to chunk. I can't just right-click and hit empty trash. Nothing happens :P lol.

---

### Post by taurus on 2007-03-09
You mean something like this from a terminal!

```
rm  ~/.Trash/*
```

---

### Post by Redeyes_Gambit on 2007-03-09
Ok, that got most of it. Thanks! However I still have 4 things left:

greg@ubuntu-laptop:~$ sudo rm  ~/.Trash/*
Password:
rm: cannot remove `/home/ubuntu/.Trash/Grounation-0.3': Is a directory
rm: cannot remove `/home/ubuntu/.Trash/kiba-dock': Is a directory
rm: cannot remove `/home/ubuntu/.Trash/vmware-server-distrib': Is a directory
rm: cannot remove `/home/ubuntu/.Trash/vmware-server-distrib (copy)': Is a directory

---

### Post by yigal.weinstein on 2007-03-09
you just need to add the recursive option on rm, [SIZE="5"]-r[/SIZE]

```
rm -r ~/.trash/*
```

---

### Post by taurus on 2007-03-09
```
rm -rf  ~/.**Trash**/*
```

---

### Post by Redeyes_Gambit on 2007-03-09
Many thanks! That did it :)

---

