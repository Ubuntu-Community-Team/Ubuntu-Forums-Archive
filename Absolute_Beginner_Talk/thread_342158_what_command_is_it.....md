---
title: "what command is it...."
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by je1117 on 2007-01-19
1. how to navigate to a folder that has a space in it (ie: Program Files)

2. how to get rid of the "locked" flashplugin folder that is stuck on my desktop. i do need it.

3. how to change /.wine/ to something i can see without the terminal.

THANKS.

---

### Post by meng on 2007-01-19
1
cd Program\ Files
(the \ is an "escape" character)
OR
cd Progr(then press TAB for autocompletion)

2
cd Desktop
sudo rm -r (name of folder)

3
Open file browser
ctrl-H view hidden files

---

### Post by smile_sunshine on 2007-01-19
For the first one - just put " " round the name 
> cd "Program Files"

:)

---

### Post by taurus on 2007-01-19
1.  ```
"Program Files" 
-or-
Program\ Files
```

2.  You probably need to change the ownership to you.
```
sudo chown -R **username**:**username** <directory>
```

3.  Just tell nautilus to show the hidden files.  You don't want to change ~/.wine to something else since wine needs it.

---

### Post by shareMenaPeace on 2007-01-19
> cd Pro* also works.

---

