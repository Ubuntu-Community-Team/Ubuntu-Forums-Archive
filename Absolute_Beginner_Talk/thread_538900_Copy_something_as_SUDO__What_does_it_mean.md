---
title: "Copy something as SUDO : What does it mean?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by sdim on 2007-08-30
Hello everybody.
What does "copy the file as sudo" mean?
I'm too much of a rookie to know stuff like that.
Thank you.

---

### Post by snowjm on 2007-08-30
This means that you need to use the "sudo" command to copy the file.

Example
```

user@host:~$ sudo cp file1 file2

```

will copy file1 to file2 (overwriting file2 if it already exists) or if you specify a a different location it will copy it there.

Example2
```

user@host:~$ sudo cp file1 ../file2

```

This will make a copy of file1 in the parent directory of your current directory, and name it file2.

When using the command "sudo" it is actually enabling you to copy those files as root user. So you will usually be promted for your password before you are actually allowed to execute the command

---

### Post by mlentink on 2007-08-30
Most likely you need to copy the file to a system area, for which only superuser access is allowed
sudo means something like: "as SUperuser DO...."

---

### Post by LaRoza on 2007-08-30
> **sdim said:**
> Hello everybody.
What does "copy the file as sudo" mean?


The above instructions are the "how", here's "why".

You only have permission to write to certain areas (also read). Copying as root (sudo), is necessary when writing to a directory where you don't have write access, outside of you /home directory.

---

### Post by mlentink on 2007-08-30
> **LaRoza said:**
> The above instructions are the "how", here's "why".
Thx for adding that. It reminds me to be a bit more explanatory with questions like these.

---

### Post by sdim on 2007-08-30
Many thanks to all of you esteemed colleagues.
So,if I want to copy a file of fonts (.ttf) to be available to Open Office,how do I specify the file(.fonts)that I want to move them into? Do I write the whole path to the file?

---

