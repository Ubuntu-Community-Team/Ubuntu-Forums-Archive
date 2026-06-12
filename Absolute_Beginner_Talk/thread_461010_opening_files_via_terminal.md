---
title: "opening files via terminal"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by eliora on 2007-06-01
i have a .sh program and i want to open a file with it from the terminal, what should my command line be?

---

### Post by Nekiruhs on 2007-06-01
```
 
cd /directory/containing/file/
nameOfFile

```
thats it

---

### Post by Blender on 2007-06-01
Do you mean opening it as if it were double-clicked from a nautilus window?

Example:
```

$ gnome-open file.pdf

```

See [this blog]("http://ubuntu.wordpress.com/2006/12/16/gnome-open-open-anything-from-the-command-line/")

---

### Post by eliora on 2007-06-01
thanks, i tried that, but i need to use the program to open the file


i was thinking of something like

chmod 755 program name
./program name filename

but that doesnt work

or 
awk -f program file

but its not in awk

---

### Post by Blender on 2007-06-01
OK. 
What does your sh script do? Whatever you write after the
program name gets passed to the script/program and it's
 up to it to decide what to do.

---

### Post by Outrunner on 2007-06-01
What do you mean? Did you try

```
./filename.sh
```

---

### Post by eliora on 2007-06-01
basically i have a file called KAR:1996
i want to run ConvertSegy2mseed.sh using the data in KAR:1996

---

### Post by Blender on 2007-06-01
Well, then it should be something like:
```

$ chmod +x ConvertSegy2mseed.sh
$ ./ConvertSegy2mseed.sh KAR:1996

```

But note that this all depends on what the script (the sh file) does. If it is supposed to work that way, then it will.

If the above commands don't work, then consider posting the contens of the **ConvertSegy2mseed.sh** file.

---

### Post by hillbilly on 2007-06-01
Blender is right, it would depend on how the install.sh is coded.

usually when my sh script is reading data from another file all I have to do is
> $ file.sh < *datafile*

maybe it would work for you.

---

