---
title: "how to open *.sh files"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by muldengold on 2008-03-20
Hi,
I just downloaded a software as a .sh file. How do I open it????
Thanks in advance.

---

### Post by Nythain on 2008-03-20
to run it...
if you are in the directory its located then
./whatever.sh should work
if you arent in the directory maybe try
sh /path/to/whatever.sh
but i could be wrong on that

---

### Post by muldengold on 2008-03-20
It tries to open it with the text editor. What kind of file is the .sh? Is it an archive? I tried it with the archive manager but it didn't work either. Any other thoughts???
thanks

---

### Post by alexforcefive on 2008-03-20
Opening a terminal and running it from there is probably the easiest method. Or you could right click > properties > permissions > allow executing file as program.

I think :D

---

### Post by Nikhil Gohil on 2008-03-20
sh files are shell scripts.try  ```
sudo chmod +x filename
``` then browse to the directory and ```
./filename
``` or ```
sh filename.sh
```

---

### Post by spupy on 2008-03-20
> **muldengold said:**
> It tries to open it with the text editor. What kind of file is the .sh? Is it an archive? I tried it with the archive manager but it didn't work either. Any other thoughts???
thanks

*.sh are shell scripts. You can open them with Gedit to view them. They contain written commands that are interpreted when you run the file in a terminal. Running the script is almost equivalent to typing in the commands from the script into a terminal one by one manually. It's like the script enters commands at the terminal instead of you, saving you time and effort.
But be aware that these scripts may contain commands that are harmful to your data. Just to be on the safe side, open the *.sh file in question with Gedit, copy its content and paste it in a post here - we will tell you what the script does and if it safe to execute it on your computer.

---

### Post by muldengold on 2008-03-20
"Or you could right click > properties > permissions > allow executing file as program."
This worked, thanks all for your help!

---

