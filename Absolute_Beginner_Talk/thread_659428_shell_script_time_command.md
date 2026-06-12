---
title: "shell script time command"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Adaptor on 2008-01-05
Hello i'm writing a little shell script so that when i log on to my computer it say somthing like "hello and welcome the time is now (time goes here) or the day is now(day goes here)"  Does anyone know the time command or script code?  Thanks for the help!

---Adaptor

---

### Post by p_quarles on 2008-01-05
The command is simply:
```
date
```
You can control the output format by specifying certain elements. E.g., for current hour (on 12hr clock) and minute:
```
date +%l:%M
```
See the manual page:
```
man date
```
for a full list of valid formatting options.

---

### Post by Adaptor on 2008-01-05
I tryed "date" and things like "-d" but i can't get it to work while testing the script in the terminal.  Here's an example of what it could say

#!/bin/bash
#logon talking script

echo " Hello How are you on this fine fine (date)"

I think i must being doing somthing stupid because this should be a very simple task.  Thanks for the help so far

---

### Post by rubicon on 2008-01-05
```
echo 'Hello, $USER, it is `date +%d-%m-%Y` now!'
```

---

### Post by p_quarles on 2008-01-05
> **rubicon said:**
> ```
echo 'Hello, $USER, it is `date +%d-%m-%Y` now!'
```
One pair of quotes (either the outer or inner) needs to be double. At least in my shell. :)

---

### Post by rubicon on 2008-01-05
Okay, my mistake :) 
```
echo "Hello, $USER, it is `date +%d-%m-%Y` now!"
```

---

### Post by Adaptor on 2008-01-05
O! i get it now! My first time programming and i didnt know about the (`````)  Thanks for the help p_quarles and rubicon!

---

