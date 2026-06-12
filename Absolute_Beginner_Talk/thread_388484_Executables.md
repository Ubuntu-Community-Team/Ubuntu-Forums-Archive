---
title: "Executables"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-03-19
I have opened Terminal (shell) and I attempted to launch a Linux exicutable, (not Exe or any windows extention, or Cedega would launch it) I got it from a Linux package, it says Exicutable file, how would I launch it? Thanks, I tried using Shell, but apparently I did not do it right, I also clicked it, and nothing. Thanks in advanced.

---

### Post by LanDan on 2007-03-19
it might help if you would explain what kind of file it is , there are several options .deb .rpm.tar etc.....

---

### Post by annda on 2007-03-19
if it really is executable,
./file_name
should do the trick. if it's not,
sudo chmod +x file_name
will make it executable.

does the file have an extension (like bin or sh)?

---

### Post by aysiu on 2007-03-19
What's the exact name of the file?

---

### Post by Peter1234123 on 2007-03-19
blender, doesn't give any specific extention, just underneath it says Type: Executable file

---

### Post by Peter1234123 on 2007-03-19
I tried "sudo ./blender" but it says "./blender: Error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: no such file or directory"

---

### Post by annda on 2007-03-19
blender is in the universe repositories, you can install it using adept - it will take care of all dependencies and shared libraries.

EDIT: ask again if you don't have universe repositories enabled (i don't know how to easily do that in KDE)

---

### Post by aysiu on 2007-03-19
> **Peter1234123 said:**
> I tried "sudo ./blender" but it says "./blender: Error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: no such file or directory"
Any reason you're not trying this instead?

**Step 1**:
[Enable extra repositories](http://www.psychocats.net/ubuntu/sources)

**Step 2**:
Install Blender with this [terminal](http://www.psychocats.net/ubuntu/terminal) command ```
sudo apt-get update && sudo apt-get install blender
```

---

### Post by DrOlaf on 2007-03-19
libSDL is in the repositories separately, and can be installed using the Synaptic Package Manager.  

How did you install blender, by the way? If you had done this using Synaptic, or aptitude, I would have expected libSDL to have been installed as well.

---

### Post by Peter1234123 on 2007-03-19
Thanks, Im attempting sudo apt-get update && sudo apt-get install blender right now, it's been waiting for headers for a good 3 mins :o

---

### Post by Peter1234123 on 2007-03-19
it says, E: couldn't find package blender.

---

### Post by aysiu on 2007-03-19
> **Peter1234123 said:**
> it says, E: couldn't find package blender.
Did you enable extra repositories first?

---

### Post by annda on 2007-03-19
DELETE: too slow

---

### Post by Peter1234123 on 2007-03-19
Yes, thank you, so much :)
works now

---

### Post by aysiu on 2007-03-19
For more on software installation, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

