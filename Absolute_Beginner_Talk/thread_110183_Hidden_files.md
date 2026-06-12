---
title: "Hidden files"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by nkingcade on 2005-12-30
How do I "change directory" to a hidden directory? example: I have an application that downloads to .aMule. When I use acroreader to open the file. acroreader does not see the folder. Yet, when I do an "ls -la" the folder exists. Is there a document that speaks to this? Thanks

---

### Post by Haegin on 2005-12-30
In the "Open" dialog box try right clicking and selecting "Show Hidden Files" on the menu. In nautilus just press Ctrl + H. If you want to find a folder quickly you can just start typing it and it will jump to folders of that name (so ".a" will jump to the first folder with a name beginning with ".a").

Hope this helps

---

### Post by nkingcade on 2005-12-30
Sorry, this answer did not help. But, thanks anyway:razz:

---

### Post by steve.horsley on 2005-12-30
One work-round you could do is to make a non-hidden link to the .aMule folder. This command would do it:
```

cd
ln -s .aMule aMule
```

---

### Post by Suger on 2005-12-30
In a Nautilus window,

Ctrl+L, and then type your absolute path.

---

### Post by nkingcade on 2005-12-30
Steve,

That worked fine. Thanks. Another question: I attempted to change the name of a file. I received the following error: unexpected token encountered "(" . I assume that the shell did not like the ( in the name. Is there a removal process for this problem? I attempted a -f with rename.

Neal

---

### Post by kaamos on 2005-12-30
try this:
```
mv "name one" "name two"
```

---

