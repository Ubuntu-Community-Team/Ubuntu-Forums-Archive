---
title: "[SOLVED] command line query"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by jon zendatta on 2007-08-28
When entering a command that is more than one line, how do i move cursor to beginning of next line

---

### Post by Rocket2DMn on 2007-08-28
You don't go to the next line, you can enter multiple commands on a single line by ending each command with the & symbol.  Ex:
```
ls & cat filename
```
This lists the content of the current directory and outputs the contents of the file "filename".  If you do something like
```
gedit filename &
```
You can open the file "filename" and still use the command line since it makes the gedit run in the background.

---

### Post by nitro_n2o on 2007-08-28
how to move the cursor in your command line highly depend on your shell!!! you can always use the right left button on your keyboard CTRL+A goes to the beginning on the line CTRL+E goes to the end 
If you want some great control over the shell in terms of moving around you should consider screen 
sudo apt-get install screen and then google about "screen" to know how to use it

---

