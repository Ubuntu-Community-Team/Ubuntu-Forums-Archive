---
title: "Copy and paste a folder from the command line"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Jhorra on 2007-07-02
Can anyone give me the command for this?

---

### Post by iAlta on 2007-07-02
cp

---

### Post by Jhorra on 2007-07-02
So is it cp /old_location /new_location ?

---

### Post by amrclutch1 on 2007-07-02
```

cp /home/user/file.conf /home/user/folder/file.conf

```

The "/home/user/file.conf" is the path to the file you want to copy, and the "/home/user/folder/file.conf" is the path you want to copy the file to.

Also there is a space between the two paths.

;)

---

### Post by st33med on 2007-07-02
```
cp <fromfile> <tofiledirectory> 
```

Copies the fromfile to the file directory. Replace those in <> with your preference.

---

### Post by st33med on 2007-07-02
Dang! I'm too slow!

---

### Post by Jhorra on 2007-07-02
Great!  Thanks for the help.

---

### Post by ncappel1 on 2007-07-02
one thing to add: the "cp" command will copy, but will not delete the source file unless you add the appropriate flag. If you want to move it and not keep the source, you can also use the "mv" command. it works the same way: mv <source folder> <destination>

---

### Post by click4851 on 2007-07-02
you could also explore the wonders of the "mv" command, I find this one helpful as well.

---

