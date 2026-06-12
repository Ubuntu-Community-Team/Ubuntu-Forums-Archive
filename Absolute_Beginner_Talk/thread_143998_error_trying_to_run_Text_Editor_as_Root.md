---
title: "error trying to run Text Editor as Root"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Tortanick on 2006-03-13
I use the Run as diffrent user aplication, however when useing the Text Editor or any text file i get the error:

Failed to run file:[directory]
as user root:
Child terminated with 1 status

It works fine if I run it as myself but I don't have write permisions for some config files I need, please help.

---

### Post by astyanax on 2006-03-13
Open up a terminal and use sudo.

If you want to use the basic text editor, then do the following at the command line:
```
sudo gedit <file>
```

---

### Post by Tortanick on 2006-03-13
thanks, 

Just so I learn: Why wasn't my way working?

---

### Post by astyanax on 2006-03-13
From what I've read and what I've tried to do in Ubuntu, the OS has the root account locked down by default.  You can't log into Ubuntu as root or run any applications as root.  There's a way to do it, but I advise against it.  Running ANYTHING as root is dangerous.  Here's the link of how to do it if you want to:
[http://www.ubuntuforums.org/archive/index.php/t-31053.html]("http://www.ubuntuforums.org/archive/index.php/t-31053.html")

Good rule of thumb, if you need superuser access to run something, use sudo.

---

### Post by Tortanick on 2006-03-13
that explains it, I thought the run as was Sudo

---

### Post by astyanax on 2006-03-13
sudo does allow you to run a command as root, but sudo actually allows you to run as other users too.  Here is a man page on sudo if your interested:
[URL="http://www.gratisoft.us/sudo/man/sudo.html"]http://www.gratisoft.us/sudo/man/sudo.html
[/URL]

---

