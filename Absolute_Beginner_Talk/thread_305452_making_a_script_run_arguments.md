---
title: "making a script run arguments"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by KhaaL on 2006-11-23
I have made a script to run a program with the -o switch, however what happens is that the program runs, but without the switch. The command is:

./dom3_x86 -o

I've tried putting quoted around the switch only - ./dom3_x86 "-o"
I've tried putting quoted around the whole line - "./dom3_x86 -o"

Neither of them work, how should i get it to work?

---

### Post by mustang on 2006-11-23
The first line you typed up should work. Would you mind posting the source code? Or atleast the code with the switch statement?

---

### Post by KhaaL on 2006-11-23
sure, the code is:
> 
#!/bin/bash
cd /media/hdc1/xtra\ installs/games/dom3/
#"/media/hdc1/xtra\ installs/games/dom3/dom3_x86" -o"
./dom3_x86 -o

---

### Post by mustang on 2006-11-23
Hm I'm kind of confused. You want your script to execute those two shell commands. So it's not up to the script to handle the switches--it's whether the dom3_x86 executable takes in switches and if so, if "-o" is a valid one.

Did you try a command like

```

./dom3_x86 --help

```

Most programs will display a list of valid parameters if you pass them the --help switch.

---

