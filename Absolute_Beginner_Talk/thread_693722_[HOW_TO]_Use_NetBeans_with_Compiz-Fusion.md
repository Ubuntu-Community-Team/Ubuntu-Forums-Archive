---
title: "[HOW TO] Use NetBeans with Compiz-Fusion"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-02-11
NetBeans doesn't work properly with composite desktops. This is a simple way to make it work without disabling desktop composition forever. I have assumed that you are using NetBeans 5.5 and compiz-fusion as your WM.

[SIZE="5"]1. Switching to metacity[/SIZE]
Open a terminal and type:
```
metacity --replace
```


[SIZE="5"]2. Downloading and installing NetBeans[/SIZE]
Open a terminal and type:
```
$sudo apt-get install netbeans5.5
```
Wait for the packages to install. After installation, fill in all the configuration windows.


[SIZE="5"]3. Creating the WM switching script[/SIZE]
Open a terminal and type:
```
$mkdir /home/username/.wmscript
$gedit /home/username/.wmscript/script.sh 
```
Replace *username* with your user-name. Now in the gedit window, type in the following code:
```
#!/bin/bash
metacity --replace &
sudo /usr/bin/netbeans
compiz --replace &
```
If you have AWN dock installed, also add these 2 lines:
```
killall avant-window-navigator
avant-window-navigator
```
Save the file and close gedit.
*Note: This would start NetBeans as root.*

Now in the terminal, type:
```
sudo chmod 0755 /home/username/.wmscript/script.sh
```
Close the terminal window.

[SIZE="5"]4. Editting the launcher[/SIZE]
Right click on the Ubuntu menu and select "Edit Menus". Click on the "Programming" option in the left panel. Right click on NetBeans in the right panel and click Properties. There in the "Command" text area, remove the existing entry and type in:
```
/home/username/.myscript/script.sh
```
And press "Close". Close the "Main Menu" window.

[SIZE="5"]5. Running NetBeans[/SIZE]
Click on Applications->Programming->NetBeans. You WM will change to Metacity and NetBeans will start. When closed, your WM will be changed back to Compiz-fusion.

---

### Post by NNG on 2008-03-11
Thanks, this post was a big help to me.

---

### Post by sayakb on 2008-03-18
> **NNG said:**
> Thanks, this post was a big help to me.

You're welcome :)

---

### Post by StOoZ on 2008-03-18
just want to know if this has anything to do with the netbeans symptoms im having...

what kind of problems this suppose to solve?

---

### Post by sayakb on 2008-03-18
When you try to run NetBeans with a composite desktop, the text and some buttons do not appear. So ofcourse, it is impossible to work upon.. This script would temporarily switch to Metacity so that NetBeans would work, and would automatically switch back to Compiz when you exit NetBeans.

---

### Post by igknighted on 2008-03-18
While this works, it is a rather ugly workaround.  See if this thread can help solve the issue rather than switching WM's just to run a program: [http://ubuntuforums.org/showthread.php?t=299335](http://ubuntuforums.org/showthread.php?t=299335)

---

### Post by sayakb on 2008-03-18
Your thread absolutely works for NetBeans, but this would work for other apps + OpenGL compliant apps..

---

