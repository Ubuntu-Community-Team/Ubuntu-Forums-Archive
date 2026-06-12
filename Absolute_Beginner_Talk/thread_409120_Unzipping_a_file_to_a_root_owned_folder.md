---
title: "Unzipping a file to a root owned folder"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Nalum on 2007-04-14
Hey I'm trying to unzip a file to /opt/lampp/phpmyadmin/theme but because it is a root owned folder I can't unzip there unless I use the sudo command in the terminal. How do I do this? I know how to change the owner of the folder but I don't want to do that.

Thanks for your help.

---

### Post by Rospo Zoppo on 2007-04-14
Extract it in a temo folder and then copy its content...

---

### Post by Compyx on 2007-04-14
> **Rospo Zoppo said:**
> Move the file to the directory by typing ```
sudo mv adresso_of_zip  directory_destination
``` and then extract it there ```
cd directory_destination
tar ......
```

You'll need sudo in front of tar too...

---

### Post by Nalum on 2007-04-14
Thanks Rospo, thats worked.
What does it mean when there is an X icon at the top right of the folder?

---

### Post by Rospo Zoppo on 2007-04-14
I think that you can't read it without admin privileges...

---

### Post by zvacet on 2007-04-14
```
sudo gunzip /directory/folder/file.gzip
```

---

