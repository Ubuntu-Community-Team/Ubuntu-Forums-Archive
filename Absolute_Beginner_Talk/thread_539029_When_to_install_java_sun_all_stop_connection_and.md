---
title: "When to install java sun all stop connection and"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Benyahoo on 2007-08-30
after tried to install update java with sysnatic and error accur lost sysnaptic also terminal and can't do any update they say to run dpkg --configure --a'  E: cash open fail

babby here new to all this 
Help please....format  hardrive mabe???:confused:

---

### Post by splintercellguy on 2007-08-30
If you can, terminal output. Just run the command in Terminal: sudo dpkg --configure -a.

---

### Post by Ubuntiac on 2007-08-30
This might be nothing, but I just noticed that you had an extra hyphen in what you typed. It's usually:

sudo dpkg --configure -a (<--Note the single hyphen before the a)

you could also try:

sudo apt-get install sun-java6-jre

At least if there's an error here, you should get a bit more information from the command line. Good luck!

---

