---
title: "saving terminal output?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2007-01-18
I'm running a program that outputs a lot of information, but as of yet haven't been able to find a way to save that information through the program settings itself.  Is there a terminal command that will copy terminal output and save it as a text file?

---

### Post by reverseninja on 2007-01-18
[This]("http://tldp.org/LDP/abs/html/io-redirection.html") may be of some help.

---

### Post by Richard Kut on 2007-01-18
Hello oscar78! I believe that the script command might do what you need. At a command prompt do this:

man script

This will give you a description of what the command does. I hope that it works for you. Good luck!

---

### Post by jd65pl on 2007-01-18
```
command > *output/filepath.txt*
```

This command will output the command to the text file specified you could try my example below to see if it is what you want

```
ls -sh ~ > ~/fileList.txt
```

---

### Post by davebgimp on 2007-01-18
> **reverseninja said:**
> [This]("http://tldp.org/LDP/abs/html/io-redirection.html") may be of some help.

Nice link.

---

### Post by kebes on 2007-01-18
The options others have mentioned should work. Another one is the command "[tee]("http://unixhelp.ed.ac.uk/CGI/man-cgi?tee")", which lets you direct stdout to be displayed both in the terminal, and simultaneously saved to a file. You can add things like "2>&1" to include error output in stdout, so that they are saved in the file too.

---

