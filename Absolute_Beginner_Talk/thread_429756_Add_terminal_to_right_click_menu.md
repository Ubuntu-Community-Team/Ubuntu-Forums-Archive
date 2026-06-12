---
title: "Add terminal to right click menu"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Jaymac on 2007-05-01
Is it possible to add the terminal to the right click menu?

The computers in our lab at university all run RHEL4 and when you right click there is a terminal launcher, and I guess I've kind of got used to it - is it possible to do this in Ubuntu?

Had a look through gconf-editor without much success..

Thanks a lot.

---

### Post by ghandi69_ on 2007-05-01
I am uncertain if there is a way to do this under gnome/kde.  However, I do know that the window managers fluxbox, and possibly xfce come with the right click menu by default.  So if it comes down to it, you could install those managers, but I am also eagerly waiting to see if this is possible in gnome/kde.

---

### Post by floke on 2007-05-01
There's a program in the repos called something like gnome-terminal-add (not that, but something like that) that will do it for nautilus.

---

### Post by mcduck on 2007-05-01
Just install the 'nautilus-open-terminal' package, log out and back again (or run 'killall nautilus'). Now you have the terminal in your right-click menu. :)

---

### Post by Jaymac on 2007-05-01
Did the trick.  Thanks a lot!

---

### Post by Roukoun on 2008-04-25
Install **nautilus-actions** (sudo apt-get install nautilus-actions) and then go to System > Preferences> Nautilus Actions Configuration...
After this its a little more complicated but there is a guide in here that may help you: [I][http://www.techthrob.com/tech/actionconfig.php](http://www.techthrob.com/tech/actionconfig.php)
[/I]

---

### Post by Roukoun on 2008-04-25
I suggest you to read the tutor above but I will tell how to do it for the terminal and then it's the same "path" for every application you want to add in your right click menu....

As I told you before after the installation go to 
1)System > Preferences > Nautilus Actions Configuration
2)click to the **+Add** option
3)**Label:**   **Terminal** (the name that will appear for your application in the right click menu)
4)**Icon:**     (put the path of the icon you want to appear in the right click menu)
5)**Path:**     **/usr/bin/gnome-terminal**
6)go to the  **Conditions** tab
7)_check_ the **Both** option (sixth line)
8)_check_ the box **Appears if selection has multiple files or folders**  (seventh line)
9)go to the **Advanced Conditions** tab
10)_UNcheck_ the box **file Local Files**
11)create a new scheme by click on the **+** option at the right
12)_delete_  the **new scheme New Scheme Description** (in a nutshell leave empty the name of your new scheme)
13)_check_ your new scheme
14)click **OK**!!!!!!
AND YOU ARE DONE.........................

---

