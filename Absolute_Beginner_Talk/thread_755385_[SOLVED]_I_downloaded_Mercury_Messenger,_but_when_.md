---
title: "[SOLVED] I downloaded Mercury Messenger, but when I click it, nothing happens!"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by josh995 on 2008-04-14
I just downloaded Mercury Messenger for Ubuntu.

Well, I installed it and everything and now it's in my Applications. When I go to click on it, nothing happens. I click, and sit there and wait as if it's going to open, but it doesn't.

What is the problem?

Also, if I need to re-install it, how do I delete a program from Ubuntu? I'm new to it as of yesterday, so all help is appreciated! Thanks!

Edit: I'm using 8.04, if that matters. Thank you!

---

### Post by lizzard on 2008-04-14
Try to run Mercury Messenger from the  commandline. The output could help you to find the problem. 
How did you install the program? Was it a deb-file or did you install from source?

---

### Post by josh995 on 2008-04-14
> **lizzard said:**
> Try to run Mercury Messenger from the  commandline. The output could help you to find the problem. 
How did you install the program? Was it a deb-file or did you install from source?

How do I do that, run from command line?

How I installed was I went to the website and clicked "Download" and then it downloaded, when it was done, it said something about... packages? So it installed and now when I click it it doesn't open.

:(

---

### Post by lizzard on 2008-04-14
open a terminal (applications->accessories->terminal) and enter the command for starting the program.

---

### Post by josh995 on 2008-04-14
Ok, I know what the terminal is, but I'm new so I don't know what the commands are. What do I type? :(

---

### Post by lizzard on 2008-04-14
Seems, you have to start Mercury Messenger with typing "mercury" into the terminal.

---

### Post by josh995 on 2008-04-14
Thank you.

Ok, I did that, and this is what came on my screen:

josh@josh-desktop:~$ mercury
- Adding Compiz/beryl compatibility mode.
/usr/bin/mercury: line 43: java: command not found

---

### Post by lizzard on 2008-04-14
Looks like a java issue. Do you have java installed.If not do:
 ```
sudo apt-get install openjdk-6-jre
``` 
and try again.

---

### Post by josh995 on 2008-04-14
Hey, it works! Thank you so much, big help!

---

### Post by lizzard on 2008-04-14
OK, I tried to install mercury by myself and had the same issue. 
You need to have "sun-java6-jre" installed to start "Mercury Messenger"
So you have to do:
```
sudo apt-get install sun-jave6-jre
``` 
After that you have to do this:
```
sudo update-alternatives --config java 
```
Choose sun-java6-jre and "Mercury Messenger" will hopefully work.

Edit: Glad to see you managed to get the program to work without this suggestion.

---

