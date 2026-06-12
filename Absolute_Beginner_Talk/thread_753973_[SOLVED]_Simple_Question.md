---
title: "[SOLVED] Simple Question"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-04-13
How do you open the terminal in a specific folder?  I tried right-clicking but do not have an open terminal option.  I am in a DEB fold and would like to install the debs in this folder.

Edit:  I am using ubuntu with GNOME.

---

### Post by munkyeetr on 2008-04-13
Enter the following commands at a Terminal window (press ENTER after each command):
```

sudo apt-get install nautilus-open-terminal
killall nautilus

```

You should then be able to right-click on a folder and open a terminal at that directory.

---

### Post by vinceUUUU on 2008-04-13
Hello

i am new to ubuntu...

if i want to open a terminal ad get it to a specific folder.....what i do is i open the terminal....then i open the gui explorer of files...(like windows explorer)

find the file....and drag it into the terminal window....and the full path will show up......you then delete the dots at each end...and type CD infront of it....and enter

your terminal will then be in the folder you want

Vince.

---

### Post by hikujk123 on 2008-04-13
Bump.

---

### Post by hurtstotalktoyou on 2008-04-13
You don't have to open terminal in a folder--you can open a folder in terminal.

When you first run terminal (applications > accessories > terminal), you'll be in what's called your home folder (/home/yourusername).  To change directories, type in "cd directory" or "cd /directory1/directory2", etc.

Just remember, all terminal commands are case sensitive.

---

### Post by hikujk123 on 2008-04-13
when I do this it just opens that folder.  The terminal is not in it.

---

### Post by hikujk123 on 2008-04-13
thanks.

---

### Post by hyper_ch on 2008-04-13
next time use a descriptive thread title and not a generic "need help" one.

---

### Post by t1n0m3n on 2008-04-13
all you have to do is append " --working-directory=<NAMEOFDIR>" into the command section of the shortcut you are using to launch terminal.
For example:  I want to have terminal start in the /etc directory I set the command to "gnome-terminal --working-directory=/etc"

---

### Post by t0p on 2008-04-13
> **t1n0m3n said:**
> all you have to do is append " --working-directory=<NAMEOFDIR>" into the command section of the shortcut you are using to launch terminal.
For example:  I want to have terminal start in the /etc directory I set the command to "gnome-terminal --working-directory=/etc"

"All you have to do"?  Heck, that's some long-winded palaver.

How about click on the Terminal icon, then type 
```
cd /etc
```
It's a little less complicated. :)

---

### Post by t1n0m3n on 2008-04-13
> **t0p said:**
> "All you have to do"?  Heck, that's some long-winded palaver.

How about click on the Terminal icon, then type 
```
cd /etc
```
It's a little less complicated. :)

That would be the answer to the original post.  Your "solution" does nothing to contribute.
Try reading posts closer next time.

---

### Post by SlappyPappy on 2008-04-13
What's "palaver"? Is that Greek or something?  

2 funny.  :lolflag:

---

### Post by t1n0m3n on 2008-04-13
Idle talk intent on deception.

---

