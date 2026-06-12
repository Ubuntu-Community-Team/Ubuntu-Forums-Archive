---
title: "[SOLVED] Starting a program in the terminal"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by uclalinux on 2007-05-15
I would like to know if there is a way to start a program in the terminal and still be able to run other commands in that same terminal. 

Example:  if I run ```
linux@linux-destop:~$ ooffice
```

Open Office will start, but i can't us that terminal until i close open office using the gui or ```
ctrl^C
```.

Is there a way to open an application and still use the same terminal?

---

### Post by Adramelech on 2007-05-15
programName &

---

### Post by heimo on 2007-05-15
Hit *ctrl+z* to stop the job and write *bg* to make it go to the background. Or use & at the end of command to make it go to the background.
```
ooffice &
```You can prefix commands with nohup if you don't want them to quit, when parent process dies.
```
nohup ooffice &
```

---

### Post by netwerx on 2007-05-15
add the "& sign"

ie: 

firefox &

that should launch firefox but free up the terminal still.

i think this is what your asking, but i could be wrong.

edit: everyone beat me too it.

---

### Post by uclalinux on 2007-05-15
Thanks for the responses.

```
<program_name> & 
```

Was what I needed. 

Thanks

---

