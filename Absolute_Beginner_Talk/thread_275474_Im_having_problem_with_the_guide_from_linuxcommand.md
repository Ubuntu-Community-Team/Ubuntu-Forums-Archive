---
title: "Im having problem with the guide from linuxcommand.org"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-10-11
Im doing the guide from [http://linuxcommand.org](http://linuxcommand.org) but I have run into a problem. I've made it to the place where you are starting to make your own and editing other scripts. More precisly this page [http://linuxcommand.org/wss0020.php](http://linuxcommand.org/wss0020.php) it should be possible to add this command: alias l='ls -l' to .bash_profile file in my home folder. But when I start up the terminal it does'nt work. If I just write alias l='ls -l' in the terminal it works just find. The thing is it doesent work the next time I start the terminal. So why is it it doesent work just to add alias l='ls -l' to my .bash_profile file? Accourding to the guide it should work.

---

### Post by Tamil on 2006-10-11
Add it in **.bashrc** and restart terminal.

---

### Post by jincast90 on 2006-10-11
> **Tamil said:**
> Add it in **.bashrc** and restart terminal.

Thanks alot. It worked. Can anyone tell me why they tell me to put it to the .bash_profile folder in guide from linuxcommand.org when it does'nt work?

---

### Post by po0f on 2006-10-11
jincast90,

IIRC, ~/.bash_profile is only sourced when you start a log in shell, like when you log in from the terminal.  ~/.bashrc is sourced every time a bash process is started, like when you open up a terminal emulator like gnome-terminal.

---

