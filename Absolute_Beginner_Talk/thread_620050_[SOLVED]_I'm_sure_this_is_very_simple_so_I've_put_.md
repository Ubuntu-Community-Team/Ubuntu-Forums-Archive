---
title: "[SOLVED] I'm sure this is very simple so I've put it here..."
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by garyj1972 on 2007-11-22
I have created a desktop icon to run a terminal command. It's NETSTAT with a few attribs that I can never remember.

When I run it. I see the window pop-up run and disappear. But Linux is so damned fast I don't get time to see it never mind read it.

In DOS I would have used some kind of input prompt to hold the screen open, but as a newbie in Linux I'm not sure how best to approach this.

Any ideas?

Thanks in advance

Gary

---

### Post by el escocés on 2007-11-22
You could always write a script and run the script in terminal.

```
vim (or any other text editor) netstat.sh
```

In vim

```
#! /bin/bash

netstat -a xxxx
```

make the script executable

```
chmod +x netstat.sh
```

then run the script when you want to run netstat

```
./netstat.sh
```

---

### Post by kpkeerthi on 2007-11-22
You may put 
```

#! /bin/bash
netstat -a xxxx
pause 'Press any key to continue&#8230;'

```
at the end of the shell script so it waits for a key stroke before it closes itself (useful especially when you want the script to run by double clicking on it).

---

### Post by garyj1972 on 2007-11-22
I get 

bash: pause: command not found

---

### Post by kpkeerthi on 2007-11-22
Try ```
read -p "Press any key to continue&#8230;"
```

---

### Post by kpkeerthi on 2007-11-22
Sorry I'm not in front of Ubuntu to try it out for you

---

### Post by garyj1972 on 2007-11-22
Thanks guys, between you I have the perfect solution. Cheers Gary

---

### Post by el escocés on 2007-11-22
```
#! /bin/bash

netstat -a
read -p "press enter to exit..."

```

---

