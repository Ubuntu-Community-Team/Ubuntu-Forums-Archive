---
title: "Howto exit X - error"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by corlex on 2005-11-27
Hello.

I am going into X (ctrl+alt+f1) and when i want to go out form there again I type startx to try to get out of it, but then i get error message.

................sudo startx
xauth: creating new authority fille /home/henrik/ .serverauth.7950
xauth: /home/henrik/ .Xauthority not writeable, changes will be ignored.
xauth: error in locking authority file /home/henrik/ .Xautority
xauth: error in locking authority file /home/henrik/ .Xautority
xauth: error in locking authority file /home/henrik/ .Xautority

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/ -X0-lock
and start again.

I installed linux yesterday for the first time, so i hope there is anyone that can help me to exit X without rebooting the computer.
I has also tried to type ctrl+alt+backspace without any help.

plase help me :)

---

### Post by dubz on 2005-11-27
at grub, press esc then select recovery mode

---

### Post by crispingatiesa on 2005-11-27
[QUOTE=corlex]Hello.

I am going into X (ctrl+alt+f1) and when i want to go out form there again I type startx to try to get out of it, but then i get error message.

................sudo startx
xauth: creating new authority fille /home/henrik/ .serverauth.7950
xauth: /home/henrik/ .Xauthority not writeable, changes will be ignored.
xauth: error in locking authority file /home/henrik/ .Xautority
xauth: error in locking authority file /home/henrik/ .Xautority
xauth: error in locking authority file /home/henrik/ .Xautority

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/ -X0-lock
and start again.

I installed linux yesterday for the first time, so i hope there is anyone that can help me to exit X without rebooting the computer.
I has also tried to type ctrl+alt+backspace without any help.

plase help me :)[/QUOTE]



ctrl+alt+F4

---

### Post by paulozzzz on 2005-11-27
I do not care about exiting X server.  I just press CTRL+ALT+Fn where n is any number between 1 and 6 for the other 6 virtual consoles (all of them are text only).  X server runs in the 7th virtual console.

Once in the other virtual consoles, such as 1st, simply press ALT+F7 to return to the graphical environment.

---

### Post by ssam on 2005-11-27
X is the graphical interface(also know as a gui) (well really is the graphics server), and usually runs at ctrl+alt+f7 (or sometimes f8)

the while text on a black background is the termial or console or command line (sometimes cli command line intergace). these are usually on ctrl+alt+f1 to ctrl+alt+6. you can also have a virtual terminal running in a window in X

if you dont have X running then you can start it with
```
startx
```
from a command line. (it is possible to run multiple X servers but it takes a bit of work)

---

