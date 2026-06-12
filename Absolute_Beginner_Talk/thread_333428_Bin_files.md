---
title: "Bin files"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Head of Stone on 2007-01-07
I am trying to install a bin file but does nothing when i try to get it to run. Also, inside terminal what is the run command.

---

### Post by aysiu on 2007-01-07
What's the program you're trying to install?

---

### Post by rejser on 2007-01-07
chmod +x filename.bin (makes the files executable)
sudo ./filename.bin (runs the file as super-user 'root' as often is required when installing a bin)

---

### Post by Head of Stone on 2007-01-07
> **rejser said:**
> chmod +x filename.bin (makes the files executable)
sudo ./filename.bin (runs the file as super-user 'root' as often is required when installing a bin)

This is what i get:
stephen@SoulSeeker:~$ chmod +x planeshift_cbv0.3.017.bin
chmod: cannot access `planeshift_cbv0.3.017.bin': No such file or directory

Then i tried just copying and pasting the file. and it loaded it might work for my graphics driver to but the are .run extentions

Thanks for that. I was about to give and use windows. Information of the basics of linux/ubuntu?

---

### Post by rejser on 2007-01-07
actually to correct myself, it should be
sudo chmod +x filename.bin (unless it's a bue/bin cd-image media)

---

### Post by Head of Stone on 2007-01-07
After doing that i now cannot access any of the files. It says i do not have permissions. to view, read, write. Wierd or normal. Solutions.  


Oppps

---

### Post by IYY on 2007-01-07
First, you must be in the correct directory, where the file is located (remember that cd is used to change directory, and ls is used to list the contents). You don't need sudo to make a file executable.

---

