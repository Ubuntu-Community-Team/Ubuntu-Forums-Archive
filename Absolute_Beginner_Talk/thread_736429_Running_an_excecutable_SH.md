---
title: "Running an excecutable SH"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by joequincy on 2008-03-26
I've been searching Google to no avail so far... and obviously haven't found an answer. I've got a game (Lux Delux, for those of you familiar with it) that is opened by executing a .sh file.

When I open the file (either by a link I've set up on the Desktop, or by double-clicking the file) I get a dialog asking me whether I want to view it in a text editor, run it in Terminal, or just Run it. What I want to do is automatically choose the "Run" option, whether by  modifying the link, or setting up a shortcut in the Applications menu.

I don't know how much information you'll need, so I'll just say that I'm running Ubuntu 7.10 and leave anything else for you to ask me. (fyi, I *am* a total newb. Just set up Ubuntu on a Parallels VM about 4 hours ago and I've been screwing around getting acquainted with it since then).

---

### Post by p_quarles on 2008-03-26
Linux looks for executables in a pre-defined path. To run something not in the default path, you would go to the directory in which the script resides and type:
```
./Lux.sh
```

---

### Post by joequincy on 2008-03-26
That seems like a 2-line terminal command to me (and yes, I just did this in Terminal)

```
cd /usr/games/LuxDelux
./Lux.sh
```

How can I simplify that down to the one line I can include in a menu item in the Application menu (screen1.png)... or what would I do to pass those commands from a link (screen2.png and screen3.png)?

---

### Post by p_quarles on 2008-03-26
A desktop launcher would simply need to specify the full path:
```
/usr/games/LuxDelux/Lux.sh
```

---

### Post by joequincy on 2008-03-26
That's what I originally tried, but it comes up with that alert from screen.png when I try it. I'm attempting to avoid that.

---

### Post by p_quarles on 2008-03-26
What's the output of this command?
```
ls -l /usr/games/LuxDelux/Lux.sh
```

---

### Post by joequincy on 2008-03-26
```
-rwxr-xr-x 1 joequincy joequincy 1153 2007-12-12 00:54 /usr/games/LuxDelux/Lux.sh

```

I ended up writing a small "test.sh" file that runs the two terminal commands you gave me before, and setting the application menu item to run that.
It works fine for me that way.

---

