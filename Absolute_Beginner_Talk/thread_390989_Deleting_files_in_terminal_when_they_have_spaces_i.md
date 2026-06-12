---
title: "Deleting files in terminal when they have spaces in their names"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by FITorion on 2007-03-22
Well like the title says...

I have files I want to delete... they have spaces in their names so ... 

like I type sudo rm MY FILE

it says no such file MY
no such file FILE

What do I do?



The reason I'm doing this in terminal is because it won't let me delete in the gui.  It says I don't have the right permissions... and since they have spaces in their names I can't change the permissions. I also can't rename them.

---

### Post by mrmonday on 2007-03-22
```
sudo rm my\ file
```

Try that.

---

### Post by nik on 2007-03-22
well, if you're in the same folder as the file, just type the first letters and then press <tab> for autocompletion (sudo rm MY<tab>).

The proper syntax would be sudo rm MY\ FILE

You can also gksudo nautilus to start a file manager with admin rights.

---

### Post by rggavubt on 2007-03-22
Put file name in quotes.  Linux doesn't like spaces in file names.  I think you can also put slash / at front and back of file name.

---

### Post by Bachstelze on 2007-03-22
Everything was said, let's say the file is "/foo bar", you can either :

-> Put the filename between quotes : *rm "/foobar"* or *rm /"foo bar"*

-> Put a **back**slash befor the space : *rm foo\ bar*

-> Use tab : *rm foo<tab>*

---

### Post by FITorion on 2007-03-22
> **nik said:**
> well, if you're in the same folder as the file, just type the first letters and then press <tab> for autocompletion (sudo rm MY<tab>).

The proper syntax would be sudo rm MY\ FILE

You can also gksudo nautilus to start a file manager with admin rights.

[SIZE="3"]
gksudo nautilus[/SIZE]

Oh man Thank YOU!  That right there end so many head aches you have no idea

---

### Post by nik on 2007-03-22
You're welcome. But be very careful, this lets you really f**' up your system without warning...

---

