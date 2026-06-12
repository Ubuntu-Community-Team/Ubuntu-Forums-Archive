---
title: "how to copy file to root folder"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by ubuhan on 2008-03-20
How do I copy file to root folder?  

Thnks,

:)

---

### Post by Het Irv on 2008-03-20
```
sudo cp 'filepath1' 'filepath2'
```

just remember to replace the single quotes with the file paths.

What do you need to copy?

---

### Post by jan quark on 2008-03-20
what do you mean by root folder?

to copy files use
```

sudo cp path/to/file path/to/new/location
```

---

### Post by Faud on 2008-03-20
Do you mean copy to your "home" folder ? or copy as root ? both are mentioned above or if you are using a gui you can just drag and drop OR you can use your file browser as root with ```
gksudo nautilus
```

---

### Post by Oldsoldier2003 on 2008-03-20
just as a comment... usually there are not many good reasons to copy a file to the root directory. At least not if you are in the Absolute Beginners Forum :)

---

### Post by aysiu on 2008-03-20
This should help you:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

