---
title: "hi total newby...making a scipt i think"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by mastercare on 2006-06-29
just getting into linux and found ubunti the most friendly so far..
i have installed a cod 2 game server on machine and this sounds stupid want to be able to click on a desktop icon and run my server...as it is my son is going into terminal and typing loads lines and then it runs fine ;earned a bit abt firestarter aswelll...as i said this is a silly question which im sure has an easy answer..
cheers
mastercare

---

### Post by Luke771 on 2006-06-29
First of all, you could try to write your questions in a little more understandable way (no offense) I mean, it's not easy to understand what the problem actually is.

Anyway, if what you want is to click an icon instead of running a command line, you can right click the panel (Linux equivalent of the Windows "task bar") choose "add to panel" and then "custom launcher".
In the "command line" field (third from the top, after "name" and "comment") you can type the command line that you would run in the terminal.
click on the box that reads "no icon" to choose an icon (optional: if you don't do that it will still be clickable)
What you get is a panel icon that you can click to run that command line, so you don't have to open the terminal  and type the line each time.
If it doesn't work, you can edit the properties by right-clicking your new icon and changing something (try checking and unchecking "run in terminal" some applications must be run in terminal)
In case of apps that have to be run as "super user" you can add "gksudo" (no quotes) before the line.
I hope this was what you were talking about...

let's make an EXAMPLE:

Let's say that you want a clickable icon that opens the file browser as root:

1 - right-click on a panel and choose "add to panel"
2 - in the windows that pops up, highest up, click the button "custom application launcher"
3 - the first filed from the top (Name): leave it blank or type a name like "File Browser" 
  - second field (comment) leave it blank or add some short comment
  - **third field (command line]: type "gksudo nautilus"**
4 - click "no icon", a window pops up, choose an icon (optional)
5 - after choosing your icon, click "close"
6 - click your new icon and check wheter it works.

You may have noticed that all the points are optional **but one**: the command line. That's the only thing that you must type or the system wouldn't know what to run.

So the short version of our example would be:

1 - right click the panel and choose "add to panel"
2 - click "custom application launcher"
3 - in the third field from the top (command line) type: "gksudo nautilus" (no quotes), leave all blank all other fields.
4 - click "close"

---

### Post by mastercare on 2006-06-29
thanks for your info...we have added the shortcut to the desktop but its not keeping the terminal box open? when you click icon it pops up for a few seconds then closes....

 we type it from an open terminal the app is fine
cheers agn 
mastercare

---

