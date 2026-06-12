---
title: "how to create a link of application on desktop"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by aleskm on 2006-06-01
Could somebody explain to me how I can create a link to an application on a desktop ? I have installed Midnight commander, but it didn't appear in "start menu" and I don't want to run terminal and write mc there everytime

thx

---

### Post by LAurel on 2006-06-01
Here's an example on how to create a shortcut to gedit:
[list][*]right-click anywhere on the desktop
[*]select "Create Launcher"
[*]in the "Name" field, type the name you want to give to the shortcut, such as gedit
[*]in the "Command" field, type the path to the executable, in this case /usr/bin/gedit
[*]make sure the "Type" is set to "Application"
[/list]

So, you need to know where the MC executable is. It'll probably also be in /usr/bin, just search for it.

---

### Post by aleskm on 2006-06-01
thx for help, these steps work for gedit but not for mc. nothing happens when I click on created shortcut. any idea why ? I looked at attributes of /usr/bin/mc ...

-rwxr-xr-x 1 ales root 657724 2005-11-01 16:44 mc

---

### Post by ComplexNumber on 2006-06-01
[quote=aleskm]thx for help, this steps work for gedit but not for mc. nothing happens when I click on created shortcut. any idea why ? I looked at attributes of /usr/bin/mc ...

-rwxr-xr-x 1 ales root 657724 2005-11-01 16:44 mc[/quote]
because the name of the program is probably wrong. don't forget that its case sensitive. also, you don't need to type in the whole path - any program in /usr/bin is already in your path (on the commandline, type in 'echo $PATH' to see for yourself), so you only need to state the exact name of the program.

---

### Post by aleskm on 2006-06-01
I've got it. mc must run in terminal. when I check "run in terminal" in properties of shortcut, its OK and the MC start after doubleclick on the shortcut. :-)

---

### Post by ComplexNumber on 2006-06-01
[quote=aleskm]I've got it. mc must run in terminal. when I check "run in terminal" in properties of shortcut, its OK and the MC start after doubleclick on the shortcut. :-)[/quote]
is mc what you really want, though? i thought you meant the old gmc or something. why don't you use a GUI instead - check out gnome-commander([click]("http://gnomefiles.org/app.php?soft_id=1279")). or there's tux commander ([click]("http://gnomefiles.org/app.php?soft_id=273"))

---

### Post by aleskm on 2006-06-01
thx for the tip. Gnome commander looks good :-)

---

