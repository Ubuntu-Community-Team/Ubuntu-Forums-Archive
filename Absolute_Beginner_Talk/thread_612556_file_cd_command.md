---
title: "file cd command"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by everest on 2007-11-14
What would be the output if I typed **file cd** in the terminal?
I get an error message, what is the reason I cannot perform this operation?

---

### Post by kpkeerthi on 2007-11-14
It is because the file command is looking for a file by name 'cd' in the directory you are running the command. If you want to check where the 'cd' program lives, do "which cd' (without quotes) and then run the file command on the full path it prints out.

---

### Post by AkGw on 2007-11-14
command "which cd" do not take effect . 
why ?

xxx@D10SERV:~/src$ sudo which cd
xxx@D10SERV:~/src$ 

nothing happend affter command

---

### Post by zvacet on 2007-11-14
```
whereis cd
```

```
locate cd
```

or go to the top of filesystem with **cd /** and 

```
sudo find / -name *cd*
```

---

