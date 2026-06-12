---
title: "The Noobs Guide to Bash-Scripting - Part 1"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by penguinboy08 on 2008-04-03
Hey, I'm currently writing a series to help beginners learn how to write bash scripts. This link goes to the first installment of the series. Please note, this is aimed at the absolute beginners, and so it starts off very basic.

[_CLICK HERE_]("http://penguinboy08.blogspot.com/2008/04/noobs-guide-to-bash-scripting-part-1.html")

Hopefully this can be of some use!

---

### Post by joshrobinson on 2008-04-03
very basic is right, but you gota start somewhere.
keep us updated

---

### Post by marckie on 2008-04-03
> **penguinboy08 said:**
> Hey, I'm currently writing a series to help beginners learn how to write bash scripts. This link goes to the first installment of the series. Please note, this is aimed at the absolute beginners, and so it starts off very basic.

[_CLICK HERE_]("http://penguinboy08.blogspot.com/2008/04/noobs-guide-to-bash-scripting-part-1.html")

Hopefully this can be of some use!

Nice!!!:)

---

### Post by ghostdog74 on 2008-04-03
1) if you don't use chmod +x to make your file executable and if there is no shebang line, you can also execute shell scripts using the shell interpreter itself. 
eg # bash myscript.sh
eg # sh myscript.sh

2) /usr/local/bin , /usr/bin, /usr/sbin are usually not a good place to store user  created scripts. mostly for 3rd party software instead. Its best to create a user directory (or use /home/user, /export/home/user etc) and put all the scripts there. then set the PATH to point to it.

---

### Post by penguinboy08 on 2008-04-03
> **ghostdog74 said:**
> 1) if you don't use chmod +x to make your file executable and if there is no shebang line, you can also execute shell scripts using the shell interpreter itself. 
eg # bash myscript.sh
eg # sh myscript.sh

2) /usr/local/bin , /usr/bin, /usr/sbin are usually not a good place to store user  created scripts. mostly for 3rd party software instead. Its best to create a user directory (or use /home/user, /export/home/user etc) and put all the scripts there. then set the PATH to point to it.

Thanks for the tips, I'll be sure to add your suggestions.

---

