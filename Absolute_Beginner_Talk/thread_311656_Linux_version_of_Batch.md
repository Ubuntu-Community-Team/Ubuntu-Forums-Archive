---
title: "Linux version of Batch"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by AirAshby on 2006-12-03
Two questions
What is Linux version of Windows batch file type? 
Is it the same as a windows batch file do you just type the terminal commands?

---

### Post by tribaal on 2006-12-03
Easy enough:
In linux, any text file can be a batch file provided the first line in the file is ```
#!/bin/bash
```
Then as you said, just type in terminal commands!
Remember to grant your file "execute" permission though, or you won't be able to run it (you do so by entering "chmod +x <filename>")
Hope this helps!

- trib'

---

### Post by AirAshby on 2006-12-03
I thank you very much that should help my parents perform some tasks to open there precious windows programs](*,)  using wine. lol

---

### Post by mcduck on 2006-12-03
Shell scripts are often named .sh to separate them from other text files.

Search forums for 'shell scripting' for more help. And here's one guide to basic/intermediate shell scrpits: [http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html]("http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

---

### Post by Haegin on 2006-12-03
A site I found helpful was [http://www.linuxcommand.org/](http://www.linuxcommand.org/) which covers shell scripting right from the beginning and shows you how to do if statements and loops which make your scripts much more flexible.
For input and to make the scripts look nice take a look at zenity - its a program that can generate gui message boxes in bash scripts.

---

