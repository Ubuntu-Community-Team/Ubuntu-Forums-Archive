---
title: "file permissions"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-06-25
how can i copy files in a folder like /usr/local/share in which the permission is checked only at executed

---

### Post by ProjectGod on 2006-06-25
use **sudo cp **<oldfile> <newfile>

check out how to use both utilities by 

[B]man cp

man sudo[/B]

---

### Post by FuzZy2006 on 2006-06-25
what about directories? they can be coppied the same way as the files?

---

### Post by illynova on 2006-06-25
[QUOTE=FuzZy2006]what about directories? they can be coppied the same way as the files?[/QUOTE]

Close, but not quite. What you can do is tell the cp command to copy all the files located INSIDE of a directory.


For example, lets say you have a "images" directory in your home directory. It looks like:

/images/house.jpg
/images/rabbit.jpg
/images/photos/me.jpg
/images/painting/mountain.jpg


Now, what you CAN do is this:

```

cp ~/images/* ~/my_new_directory

```

This is will copy all files inside of the images directory, namely house.jpg and rabbit.jpg. If you want to recursively copy EVERYTHING inside of images, you'll need to do:

```

cp ~/images/* ~/my_new_directory -R

```

Now everything in images will be in my_new_directory. Give it a try, and ask away if you have more questions about cp :)

---

### Post by raptros-v76 on 2006-06-25
no. all you need to do to copy a directory is
```
 cp -r <directory to copy> <new location> 
```

---

