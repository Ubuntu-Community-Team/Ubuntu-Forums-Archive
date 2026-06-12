---
title: "Ubuntu Equivalent of &quot;Alt+Control+Delete&quot;"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by Paul133 on 2006-08-26
I'm wondering how you kill a frozen application in Ubuntu. In Windows, I'd hit alt+control+delete, what in Ubuntu?

Note: The application was unsupported (universe)

---

### Post by deadgobby on 2006-08-26
What is frozen? Any hoo 
[http://ubuntuguide.org/wiki/Dapper#How_to_restart_GNOME_without_rebooting_computer](http://ubuntuguide.org/wiki/Dapper#How_to_restart_GNOME_without_rebooting_computer)
[http://ubuntuguide.org/wiki/Dapper#limewire](http://ubuntuguide.org/wiki/Dapper#limewire)

---

### Post by Tomosaur on 2006-08-26
Alt+F4 will usually kill an application (it works a lot better than it does in windows). If you ran the program from the terminal, ctrl+c will normally close it.

You can also use System > Administration > System Monitor to get a task-manager like interface. If you prefer this, you can just bind it to a keyboard shortcut such as ctrl+alt+del.

---

### Post by christhemonkey on 2006-08-26
Or you can type, Alt+F2 and then type in 
```
xkill 
```
And then just click on the application.
In most every instances this should end the program immediately.

---

### Post by Cynical on 2006-08-26
In Automatix there is an option to do what one poster above said and bind alt+ctrl+del to the system monitor, the task manager equivalent.

---

### Post by nalmeth on 2006-08-26
I love when I get to use xkill :)

---

### Post by Paul133 on 2006-08-26
Liquid War 5.16. alt+F4 didn't work, but xkill did. I knew I remembered a command that killed Windows you clicked on, but I thought it was killall; then I tried killall and it didn't work, so thanks. And thanks for showing me that alt+F2 essentially brings up a terminal! I wanted to know the key combo for that!

---

### Post by christhemonkey on 2006-08-26
No problem :D

Ask and you shall recieve... (or something like that?!)

---

### Post by 3rdalbum on 2006-08-26
You can also add a "Kill Application" button to your Gnome panel. It works in much the same way as Xkill - click on the button then click on the window whose owner you want to kill.

---

### Post by Paul133 on 2006-08-26
Great Even easier! I love Ubuntu (and Gnome)! It's like the OS equivalent of Firefox: Open Source, secure, and customizable!

---

