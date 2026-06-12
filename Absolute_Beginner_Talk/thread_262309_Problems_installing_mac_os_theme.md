---
title: "Problems installing mac os theme"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-21
when i try this guide i got earlier the ask me to do this 

oem@haxer:~$sudo cp apple.png/usr/share/icons/hicolor/48x48/apps/disributor-logo.png
cp: missing destination file operand after `apple.png/usr/share/icons/hicolor/48x48/apps/disributor-logo.png'
Try `cp --help' for more information.

what am i doing wrong?

it says on the guid that this command may not work in dapper what should i do please :confused:

---

### Post by LotsOfPhil on 2006-09-21
You need a space between "apple.png" and "/usr/share/icons/hicolor/48x48/apps/disributor-logo.png"

The syntax of the cp command is:
cp file1 file2
It copies file1 to file2.

```

sudo cp apple.png /usr/share/icons/hicolor/48x48/apps/disributor-logo.png

```

Cut and paste that. For more info, type "man cp"

---

### Post by haxer on 2006-09-21
i get this cp: cannot stat `apple.png': No such file or directory

---

### Post by aktiwers on 2006-09-21
And when you go to the 
 /usr/share/icons/hicolor/48x48/apps/

Is there a file there called
disributor-logo.png ??

---

### Post by haxer on 2006-09-21
I have loged out that project when i was reading on the list to do .. to get the exact mac os theme i got the feeling that i wasnt capable to make it :)

---

### Post by Dinerty on 2006-09-21
If you want the MacOS Launcher, install gdesklets from Synaptic Package Manager.

Heres my desktop with the launcher bar, and some monitors

[[IMG]http://img241.imageshack.us/img241/7166/edgyeftyw4.th.jpg[/IMG]](http://img241.imageshack.us/my.php?image=edgyeftyw4.jpg)

---

