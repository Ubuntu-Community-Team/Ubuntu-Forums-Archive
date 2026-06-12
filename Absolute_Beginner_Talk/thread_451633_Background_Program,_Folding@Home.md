---
title: "Background Program, Folding@Home"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by otchster on 2007-05-22
This question is in reference to the Folding@Home program for Ubuntu, but I assume it would apply to any program..

I have a prompt.  I execute a <./program_name> command to start the program.  The program then runs, thus my prompt is gone, restricting me to enter any commands.  It I enter CTRL + C, it ends the program.

Being that Ubuntu is a multi-tasking OS, is there something I can do to get the prompt back to do other things while the program continues to run?  Also, if this IS possible, how do I return to the program?


Thanks for all info, Good Day =)

---

### Post by Jussi Kukkonen on 2007-05-22
```
./program_name &
```
That might leave you with ugly output on the screen though (if the app has output).
This should redirect the output and possible errors to logfile:
```
./program_name > logfile 2>&1 &
```

---

### Post by Sparkster185 on 2007-05-22
Alternatively, you can execute a command and then suspend it with CTRL+Z.  Once you do this, type 

```
bg
``` to send it to the background.  The terminal will notify you when the program terminates.  If you wish to bring it to the foreground, type ```
fg
```

---

### Post by otchster on 2007-05-22
> **Sparkster185 said:**
> Alternatively, you can execute a command and then suspend it with CTRL+Z.  Once you do this, type 

```
bg
``` to send it to the background.  The terminal will notify you when the program terminates.  If you wish to bring it to the foreground, type ```
fg
```


so when I do CTRL + Z, it suspends...  when i do bg it RESUMES?  and then puts it in the background, while RESUMING?

thanks

---

### Post by Jussi Kukkonen on 2007-05-24
Correct. The result of:
```
./program
CTRL-Z
bg

```
is the same as
```
./program &
```

(so you may still have the output problem)

---

### Post by Anicka on 2007-05-24
Open a new terminal-window would maybe be the very easy solution or a tab in the existing one.

---

