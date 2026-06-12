---
title: "C shell scripts"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by opticsnake on 2006-10-14
Just installed the C shell in ubuntu and created a script called colortest.csh

```
set flag
echo $flag
set color=red
echo $color
set name = Graham Glass
echo $name
set name = "Graham Glass"
echo $name
set

```

I know, it's a simple program but I'm just starting out learning scripting.  Unfortunately, I can't get it to run.  When I enter "colortest.csh" at the shell prompt, I get "colortest.csh: command not found".  I've run chmod to make sure the file is executable and checked permissions.  What am I missing?](*,)

---

### Post by IYY on 2006-10-14
chmod +x colortest.csh
./colortest.csh

Although, it will also be wise to add the line #!/bin/csh to the top of your script, so that it uses CShell to execute and not Bash.

---

### Post by opticsnake on 2006-10-14
HUGE thanks!  One other thing, how do you edit a script after it's been created?

---

### Post by Delkster on 2006-10-14
> **opticsnake said:**
> HUGE thanks!  One other thing, how do you edit a script after it's been created?

How did you create it? You can edit it with any text editor, such as Gedit (graphical) or nano (console), for example with the command
```
nano colortest.csh
```

---

### Post by opticsnake on 2006-10-14
Many thanks again.  Guess I'm not paying enough attention in class! :rolleyes:

I created my script using cat >colortest.csh

---

