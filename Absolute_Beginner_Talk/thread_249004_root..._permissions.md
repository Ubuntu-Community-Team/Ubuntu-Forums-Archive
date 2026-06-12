---
title: "root... permissions"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by babujbf on 2006-09-01
hey

I got this problem with file permissions... Im trying to add some fonts and I gotta be root but I cannot login with root in the login window.

Where do I login as root? I red a thread similar to this one and they where talking about sudo commands. Which is complete chinese to me lol since Ive been using this for like a week. So if anyone could help me out Id appreciate it.

---

### Post by SoftTaco on 2006-09-01
if your in terminal just add "sudo" to the begining of your command:

for example:
$ls /whatever
permisson denied
$sudo ls /whatever
Password:     (enter password)
results!

---

### Post by tearln on 2006-09-01
Is there a way to have root permissions w/o being in the terminal? I'm trying to copy some gimp scripts from my desktop to the gimp script folder and I don't know how to do that in the terminal.](*,)

---

### Post by bikeboy on 2006-09-01
Assuming you're using gnome, open a terminal (yeah I know what you're thinking) and type: 
```
gksudo nautilus
```

Make sure you close it when you're done.

---

### Post by LKRaider on 2006-09-01
Try this:

Press Alt+F2 and type ```
gksudo nautilus
```
This will give you a nautilus window with root permissions

---

### Post by JNowka on 2006-09-02
ATTENTION:
If you are afraid of hackers getting into your computer, don't follow through with what I am about to instruct.

When you wish to be root in a GUI and be able to do most anything I find it easiest to do the following.

CTRL + ALT + F1
login using your screen name and password
type in sudo -i
put in the root password
enter "startx -- :1" into the terminal

You now have a GUI and are root over all at the same time.
Though for some reason Ubuntu doesn't let you have access to Synaptic you can click on file install them.  Change any permissions for files and folders without chmod, etc.  The reason this is dangerous is that if a hacker attacks your computer while you are in this state, they can gain complete access to your system.  So it is a good idea to use it sparingly, or even not at all.  I just know this helped me out when at first I was a total newb.  When you are done log out as normal, you will return back to the command prompt.  enter "exit" into the console and return.  Repeat once more.  Now hit CTRL + ALT + F7.  You are now back to your screen.

---

### Post by aysiu on 2006-09-02
JNowka, that sounds interesting, but is there any advantage to that over just Alt-F2 ```
gksudo nautilus
```?

---

