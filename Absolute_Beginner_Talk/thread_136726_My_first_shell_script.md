---
title: "My first shell script"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by Spinelli on 2006-02-26
I wrote my first shell script using this guide:

[http://www.linuxcommand.org/wss0010.php]("http://www.linuxcommand.org/wss0010.php")

It is a very simple and somewhat retarded script:

#!/bin/bash
#My first script

echo "Hello World!"

I used vi to create the file. The file name is first_script. I put it in /home/sean/bin. I made it executable by typing: 

```
chmod 700 first_script 
```

It works great when i specify the absolute path. 

```
./bin/first_script
```

I don't want to specify the absolute path to make it work. When I type:

```
first_script
```

It says "command not found". I tried doing all of the above using the terminal in Gnome. (Applications--->Accessories--->Terminal)

When I logged into a different terminal (i.e. ctrl+alt+F1) I can just type:

```
first_script
```

And it works. I do not understand why this happens. I tried restarting my computer and it still didn't work in the Gnome terminal. I would greatly appreciate any suggestions or help. I am still very new to Linux. Thanks!

---

### Post by knalle on 2006-02-26
try this;

**chmod gou+x first_script**

---

### Post by 5-HT on 2006-02-26
To execute the script using only the filename and not the absolute path from a terminal emulator (i.e. gnome-terminal), you need to put the directory the script is in into your path.

In your particular case:

1. Open up ~/.bashrc in your favorite editor
2. Append this line to the file:

```
 export PATH=$PATH:/home/sean/bin 
```

3. Close the terminal, and on restarting it you should be able to execute the script by just typing the filename.


As to why it works from the start from a virtual terminal (i.e. ctrl+alt+F1), that's because by default ~/home/<username>/bin is already in the path for login shells (there are different files that are parsed for login shells vs non-login shells).

Hope that helps.

---

### Post by Spinelli on 2006-02-26
Thanks 5-HT. I did exactly what you suggested and it worked great!

---

