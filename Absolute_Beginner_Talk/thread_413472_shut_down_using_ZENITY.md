---
title: "shut down using ZENITY?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by La Hechizera on 2007-04-19
hi,

can you please tell me how to make a shortcut on a desktop to shut down using zenity (it should ask after how long time do I want to turn off the computer)? :(

---

### Post by La Hechizera on 2007-04-19
:(

---

### Post by sisco311 on 2007-04-19
make a luncher with this command:
```
sudo shutdown -P `zenity --entry --text="shutdown time (minutes or HH:MM)"`
```

---

### Post by sisco311 on 2007-04-19
```
sudo shutdown -P `zenity --entry --entry-text="now" --text="shutdown time (minutes or HH:MM)"`
```

default time is now

---

### Post by La Hechizera on 2007-04-19
> **sisco311 said:**
> make a luncher with this command:
```
sudo shutdown -P `zenity --entry --text="shutdown time (minutes or HH:MM)"`
```

I did a right-click on the desktop, then chose to create launcher. Type - program, title - zenshutdown, command - sudo shutdown -P `zenity --entry --text="shutdown time (minutes or HH:MM)"` . now when I click on the new icon it doesnt work.. what did I do wrong? :oops:

---

### Post by La Hechizera on 2007-04-19
> **sisco311 said:**
> ```
sudo shutdown -P `zenity --entry --entry-text="now" --text="shutdown time (minutes or HH:MM)"`
```

default time is now

when I enter this line it still doesn't work :-(

---

### Post by sisco311 on 2007-04-19
open a terminal:
```
sudo gedit /usr/bin/zenshutdown
```

copy and paste this:
> #!/bin/bash
sudo shutdown -P `zenity --entry --entry-text="now" --text="shutdown time (minutes or HH:MM)"`

close and exit

in terminal:
```
sudo chmod 0755 /usr/bin/zenshutdown
```

change the lunchers command to zenshutdown

---

### Post by La Hechizera on 2007-04-19
thanks, sisco! :)

---

