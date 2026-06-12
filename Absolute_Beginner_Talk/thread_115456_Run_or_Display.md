---
title: "Run or Display?"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by ned.b on 2006-01-10
I wrote a simple shell script to start an app, when I double click it I get a message-box titled "Run or Display?"  

...is an executable text file... with four options:

Run in Terminal
Display
Cancel
Run

How do I make it automatically run in a terminal?

---

### Post by bluefrog on 2006-01-10
create a link and select the desired value

james

---

### Post by ned.b on 2006-01-10
[QUOTE=bluefrog]create a link and select the desired value

james[/QUOTE]

thanks - I have created a link and when I go into the properties of the link I have two choices:

*Text editor
*Terminal

whichever I choose it makes no difference, I still get the box pop up with four options... Text Editor option can not be removed even though my user owns the link.   Am I doing something wrong?

---

### Post by ned.b on 2006-01-12
For anyone that has the same difficulty...

Create an Application Launcher to launch the script:
* right-click desktop
* click "create launcher..."
* enter a name for the launcher
* in the command: area either type in the path or browse t the script

:rolleyes: easy when you know how

---

### Post by jacrider on 2006-01-12
ned.b:  Thanks!  Works like a charm.

You're right it is easy when you know how!

---

