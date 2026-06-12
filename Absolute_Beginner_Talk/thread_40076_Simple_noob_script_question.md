---
title: "Simple noob script question"
date: 2005-06-07
forum: Absolute Beginner Talk
---

### Post by Darkelite on 2005-06-07
How do i make a new file where i can write commands in it, and then save it and run it. (By double clicking file and having it open in the terminal)

..like a batch file in windows

Thanks.

---

### Post by mtron on 2005-06-07
open a terminal

```
gedit hi
```

copy in the file 
```

#! /bin/sh
zenity --info \
        --text="strike! my first script"
```

close gedit & type

```
chmod 744 $HOME/hi
```

now run it :

```
./hi
```

What it does:
A script usually starts with "#! /bin/sh" in the first line then enter just the commands. 

a script to auto - update ubuntu would be:

```
#! /bin/sh
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

then you must make the script executeable, by ch'modding it to 744, and to start a script from terminal: ./*scriptname*

---

### Post by Darkelite on 2005-06-07
[QUOTE=mtron]open a terminal

```
gedit hi
```

copy in the file 
```

#! /bin/sh
zenity --info \
        --text="strike! my first script"
```

close gedit & type

```
chmod 744 $HOME/hi
```

now run it :

```
./hi
```

What it does:
A script usually starts with "#! /bin/sh" in the first line then enter just the commands. 

a script to auto - update ubuntu would be:

```
#! /bin/sh
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

then you must make the script executeable, by ch'modding it to 744, and to start a script from terminal: ./*scriptname*[/QUOTE]
 thanks, works great!

---

