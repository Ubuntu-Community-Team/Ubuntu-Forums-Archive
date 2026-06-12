---
title: "wget"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by msh1 on 2007-11-06
hi all 
i just starting to learn ubuntu not sure if its for me yet anyway just following  some instructions
if i type wget ? in terminal it just says no such file or folder ummm whats going on
thanks

---

### Post by Pumalite on 2007-11-06
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)

---

### Post by Fixman on 2007-11-06
Try

```
man wget
```

---

### Post by Hospadar on 2007-11-06
wget is used to download stuff (generally from the internet) from the command line, for example:```
wget http://www.yourpage.com/yourfile.zip
```

I don't know exactly what you're doing, but if you want to browse around with the command line (like if you're setting up a server with no GUI) you could try "lynx" which is a command-line web browser ```
sudo apt-get install lynx
lynx
```

---

### Post by msh1 on 2007-11-06
no still not got a clue i think wget  file must be missing can i down load it
thanks

---

### Post by nhandler on 2007-11-06
wget is used to download files from the internet. So for example, if I enter
```
wget http://google.com
```
in a terminal, it will download the html source code of the main google.com page. Or if I type
```
wget http://www.google.com/intl/en_ALL/images/logo.gif
```
It will download the logo.gif (main google logo) to my computer.

There are more advanced ways wget can be used (for example, you can mirror a site), and you can see how by typing
```
man wget
```
in a terminal.

---

### Post by msh1 on 2007-11-06
oh i see .it then down loads it to home folder. i got ubuntu cuz fed up with windows crashing etc but need to run photoshop cs 2 as part of my job i have read it will run using wine but dont seem to be able to down load it 
thanks

---

