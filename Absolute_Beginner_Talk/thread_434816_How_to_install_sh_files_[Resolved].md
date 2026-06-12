---
title: "How to install sh files? [Resolved]"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by WiRU on 2007-05-06
Okay, i downloaded this file:
install-crossover-standard-demo-6.0.1.sh
When i try to open it this cames up:
[[IMG]http://img293.imageshack.us/img293/2359/screenshot1ed7.th.png[/IMG]](http://img293.imageshack.us/my.php?image=screenshot1ed7.png)
I installed all available locales but it keeps showing up. I also tried typing "sh install-crossover-standard-demo-6.0.1.sh" in the terminal but it answered:
"sh: Can't open install-crossover-standard-demo-6.0.1.sh".
Am I doing something wrong? How do i install this file?
Thanks

---

### Post by bubble_bobble on 2007-05-06
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_01.html)

Hope this helps!

---

### Post by darkrose on 2007-05-06
make it executable then run it. Fromm the command line:
cd /directory/containing/crossover/
chmod u+x install-crossover-standard-demo-6.0.1.sh
./install-crossover-standard-demo-6.0.1.sh

---

### Post by WiRU on 2007-05-06
> **darkrose said:**
> make it executable then run it. Fromm the command line:
cd /directory/containing/crossover/
chmod u+x install-crossover-standard-demo-6.0.1.sh
./install-crossover-standard-demo-6.0.1.sh
The file is in this directory:
/home/MYUSERNAME/Desktop
When i typed this in the terminal it said:
"bash: /home/MYUSERNAME/Desktop: is a directory"
but when i typed:
"chmod u+x install-crossover-standard-demo-6.0.1.sh"
it said:
"chmod: cannot access `install-crossover-standard-demo-6.0.1.sh': No such file or directory"

No wait

---

### Post by darkrose on 2007-05-06
cd ~/Desktop

then chmod

---

### Post by WiRU on 2007-05-06
thank you very much

---

### Post by darkrose on 2007-05-06
you're welcome

---

