---
title: "How to make a shortcut to VNCviewer?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by yezzer on 2007-01-24
Hello!

How do I make a shortcut on the top bar of the desktop to the following terminal command?

vncviewer 127.0.0.1:1 -passwd ~/.vnc/passwd

That command works 100% fine in terminal.

Ive tried adding it as either an application  or application in terminal, and it doesnt work when i click it.

any ideas anyone? :)


As an aside - i want to see screen1 as a smaller window in screen0 - using VNCviewer works fine, but seems a bit silly way to do things... 
Is there another way to control screen1 from screen0? (screen1 is in a different room to screen0!)

thanks!

---

### Post by linuchsan on 2007-01-24
You can place it in the menu layout (new item), but that is the way i prefer it.

---

### Post by Buck2348 on 2007-01-24
Adding a launcher works for me except I don't have a password file set up.  Doesn't anything happen when you click on the icon?  As I said, clicking it brings up the password window for me.  Could you paste the format of the contents of your ~/.vnc/passwd file?  I don't know why I don't have one but trying to make one blind didn't work.
EDIT:  Never mind.  I ran the passwd program but can't get the command with password to work even in terminal.  :frown: 

Buck

---

### Post by hscottyh on 2007-01-24
You could right click on a toolbar, then add to panel. Select Terminal Service Client Applet. It is a front end for several clients including VNC.

---

### Post by damdim on 2007-05-07
It's an old question, but I had the same problem and I found the solution. For some reason it doesn't accept the ~/ variable so the command should be:

vncviewer 127.0.0.1:1 -passwd /home/"user"/.vnc/passwd

---

