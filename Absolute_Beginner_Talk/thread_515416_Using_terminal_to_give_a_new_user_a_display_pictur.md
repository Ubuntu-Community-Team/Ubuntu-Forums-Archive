---
title: "Using terminal to give a new user a display picture"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Genecks on 2007-08-01
Let's say I'm adding users using the adduser command. How do I assign one of the users a picture within terminal?

I do not want to use a graphical program to assign the picture.

---

### Post by mcduck on 2007-08-01
Save the picture with the name '.face' into that user's home directory.

```
mv /path/to/your/picture.png /home/newuser/.face
```

---

### Post by Genecks on 2007-08-01
Errr... not save it with the name face, but to put it in the "hidden?" directory .face ....
Right?

---

### Post by splintercellguy on 2007-08-02
You're moving the file into a new file named .face, think renaming ;).

---

### Post by mcduck on 2007-08-02
no, you save it with the name .face so it becomes a hidden file.

---

### Post by asmoore82 on 2007-08-02
you could also hard link the picture if the place it's already in is on the same partition as
their home.

```
~ $ ln /path/to/picture /home/user/.face
```

a **hard link** is one of the few filesystem structures in UNIX that has no
Windows equivalent.

In effect, two separate filenames point to the same data; and the system knows
that if one filename is deleted, the data should still remain for the other links to it.

so that if the user deletes his/her ".face" file, you still have it in its original path.

---

### Post by Genecks on 2007-08-02
Either way, the new picture isn't showing up at the login screen. I can see it in the "Users and Groups" graphical tool, though.

Anyone know how I can get it to view on the login screen using terminal commands?

---

