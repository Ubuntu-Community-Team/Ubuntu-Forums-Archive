---
title: "Frets on Fire game Help plz!"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by aznpride93 on 2008-01-27
how do i get get it to run in dream linux? the file is a shell script.

---

### Post by Fleece Flamingo on 2008-01-27
I don't really think you can. FOF is mostly designed for windows, grab the .exe and try wine.

---

### Post by emarkd on 2008-01-27
You can run a shell script from the terminal.  Click on Acessories > Terminal and run your script from there.

---

### Post by aznpride93 on 2008-01-27
> **emarkd said:**
> You can run a shell script from the terminal.  Click on Acessories > Terminal and run your script from there.
how do i run a script
the exact name of the file is "fretsonfire" if it helps

---

### Post by emarkd on 2008-01-27
If the script is just sitting on your desktop or you can find it in the file manager, you can just click on it to execute it.  From the Terminal, you'd execute it by typing it's name and hitting enter.  Remember that you have to specify the path, so if you're in the same directory as the file you'd do

```
./fretsonfire
```

---

### Post by aznpride93 on 2008-01-27
> **emarkd said:**
> If the script is just sitting on your desktop or you can find it in the file manager, you can just click on it to execute it.  From the Terminal, you'd execute it by typing it's name and hitting enter.  Remember that you have to specify the path, so if you're in the same directory as the file you'd do

```
./fretsonfire
```
the problem is, it won't execute
that's why i'm looking for a way to do it manually

---

### Post by antisocialist on 2008-01-27
move it to /home/user/
type 
chmod +x fretsonfire
./fretsonfire

if you have any question about a cmd refer to the link in my sig

---

### Post by Majorix on 2008-01-27
Maybe it is a windows exe? Or maybe it doesn't have the shebang line ie "#!/bin/bash" without quotes?

---

### Post by disturbedite on 2008-01-27
> **Fleece Flamingo said:**
> I don't really think you can. FOF is mostly designed for windows, grab the .exe and try wine.
sorry, but that is not right, there is indeed a native linux version.

---

