---
title: "Coping contents fomr one folder to another?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by lugnut_9754 on 2007-12-02
Hello. I'm trying to copy the contents of /home/michele/Music to /media/disk and every thing i try i end up having the whole folder Music copied when I just want the contents of the folder. please help!
the command I havr been using is:
cp -r /home/michele/Music /media/disk
I have tried putting the / in different places and either the same thing happens or i get an error. Any help would be greatly appriciated.

Thanks.

---

### Post by spiderbatdad on 2007-12-02
try cp -a /home/michelle...etc

---

### Post by rainwalker on 2007-12-02
You could do it graphically rather than using the command line, if you want. Just drag and drop all the files you want

---

### Post by lugnut_9754 on 2007-12-02
using cp -a and doingit graphically both dont work because it says i dont have permission even though the perimission in the properties say i can create and delete files.

---

### Post by lugnut_9754 on 2007-12-02
thanks but i got it, i figured out how to change the permissions

chmod -R 775 /media/disk/

that allowed me to copy and paste the contents

thanks

---

### Post by spiderbatdad on 2007-12-02
using the terminal you can precede cp -a with sudo to give yourself super user privileges. This is probably safer and easier than changing the permissions of your directories. There is a lot of info available to teach you about permissions in linux.

```
sudo cp -a /home/michele/Music /whatever/whatever
```

---

