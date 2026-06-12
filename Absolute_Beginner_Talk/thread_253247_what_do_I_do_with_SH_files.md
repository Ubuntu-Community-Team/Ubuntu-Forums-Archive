---
title: "what do I do with SH files?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by crunchystrike on 2006-09-08
Hello, i have downloaded 2 .sh files and I am wondering how I can use them. here are my questions:

1. What type of file is it
2. what is is used for
3. how can i open it or execute it

---

### Post by encompass on 2006-09-08
shel script is the type if I am not mistaken.
you can run them from the terminal.
./<filename>
If that does not work... make it executable first by doing..
chmod +x <filename>
what files are they?

---

### Post by amo-ej1 on 2006-09-08
Files with a .sh extension are shell script, they are simply a combination of shell logic. (you can compare them with dos .bat files). To view their contents, simply open them in a text editor. Most likely it's an auto installer of some kind (java ?, nvidia driver ?, a linux game ?). These auto installers typically contain a piece of shellcode to do the installation followed by the zip file with some logic do verify the checksum. So if you want to know what they do (and you're not scared from some shell command open them in a text editor).

In order to execute them (simply use them). You can open a console, cd to the right directory and run chmod +x file.sh (this sets the execute flag, which probably isn't there if you downloaded it from some place and then you can execute it using ./file.sh (you need the ./ because the current directory  isn't in your $PATH).

Another option is simply execut sh /path/to/file.sh in this case you don't need to set the execute bit.

---

