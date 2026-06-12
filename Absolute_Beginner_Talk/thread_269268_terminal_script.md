---
title: "terminal script"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by captainroin on 2006-10-01
ok absolute newbie question ](*,) . i know i've seen it before but how do i make a script to run a program through the terminal.

example: i have to type WINEDLLOVERRIDES=wintab32=n wine "C:\\Photoshop\\Photoshop.exe" to get photoshop to run with wine. how do I add that to the applications menu? i tried it with alacarte but i'm not sure how that's suppposed to work.

thanks in advance

---

### Post by NESFreak on 2006-10-01
in alacarte "file" "new item" and at "command" type your command, give the link a name, maybe a description, or even an ico. thats is.

---

### Post by skymt on 2006-10-01
I'm not sure Alacarte will handle the environment variable properly. Here's the script version:```
#!/bin/bash
WINEDLLOVERRIDES=wintab32=n wine "C:\\Photoshop\\Photoshop.exe"
```Put that in a file (anywhere) and make it executable through Nautilus properties or "chmod +x scriptname" in a terminal. Then put the path to the script in the command field of Alacarte.

---

### Post by captainroin on 2006-10-01
> **skymt said:**
> I'm not sure Alacarte will handle the environment variable properly. Here's the script version:```
#!/bin/bash
WINEDLLOVERRIDES=wintab32=n wine "C:\\Photoshop\\Photoshop.exe"
```Put that in a file (anywhere) and make it executable through Nautilus properties or "chmod +x scriptname" in a terminal. Then put the path to the script in the command field of Alacarte.


thats the one i was looking for! thanks.

---

### Post by captainroin on 2006-10-01
ok... one more thing...

i made it executable but when i click on it it asks if i want to run it or display its contents. is there a way to remember what i say and do it everytime? or do i have to click the same button everytime.

thanks again

---

### Post by skymt on 2006-10-01
> **captainroin said:**
> ok... one more thing...

i made it executable but when i click on it it asks if i want to run it or display its contents. is there a way to remember what i say and do it everytime? or do i have to click the same button everytime.

thanks again

You can't set that for each file, but you can set it universally. Open a file browser window, go to Edit > Preferences > Behavior, and under "Executable Text Files", select "Run executable text files when they are clicked".

---

### Post by captainroin on 2006-10-01
awesome. thanks again.

i appreciate the help everyone gives on this forum. :KS

---

