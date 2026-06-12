---
title: "how to create shortcut"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by sthapit on 2007-05-27
Hi.  Is it possible to create a shortcut so that I can type ss instead of typing ruby script/server?

---

### Post by throntax on 2007-05-27
yeah, using the terminal, you can create a shell script! 
start a file called ss using your favourite text editor
begin the first line with 
#!/bin/bash

then after that write the command you want 'ss' to run.
Save the file and make it executable with chmod a+x ss
and move the file into a place that other binariesgo, like /usr/local/bin

now when you run ss, whatever you've written in the file gets run!

---

