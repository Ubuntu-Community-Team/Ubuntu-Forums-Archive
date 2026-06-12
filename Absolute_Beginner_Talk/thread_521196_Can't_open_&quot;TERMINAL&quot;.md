---
title: "Can't open &quot;TERMINAL&quot;"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by jamboyoungy on 2007-08-09
Hi there

I have just installed Xubuntu *fiesty faun* but when I try to open ***Applications-Accessories-Terminal*** the screen turns black with some text, then immediately returns and makes me log in with my username and password again, without ever opening the terminal program.

Can anybody help?

---

### Post by jamboyoungy on 2007-08-09
Anyone?

---

### Post by splintercellguy on 2007-08-09
Hmm, strange indeed. Somehow invoking the Terminal is causing the X server to restart. Are you using any restricted graphic drivers?

---

### Post by AnRa on 2007-08-09
It's a bug, a workaround is changing the color depth to 16.

---

### Post by e6626550w on 2007-08-09
> **jamboyoungy said:**
> Hi there

I have just installed Xubuntu *fiesty faun* but when I try to open ***Applications-Accessories-Terminal*** the screen turns black with some text, then immediately returns and makes me log in with my username and password again, without ever opening the terminal program.

Can anybody help?

There is a bug in the program. Easy way around it is to just use xterm which is included. Alt-F2 which brings up what they call the 'run program' and you can type in xterm and click run and a small terminal will appear. Can't copy and paste though in this terminal or at least you can't without knowing more about this old terminal program than you probably want to learn so the next thing to do is to modify your /etc/X11/xorg.conf file. 

Modify the 'depth' setting in the 'screen' section of the file to 16. It probably says 24 right now and you're set. i had to change 2 lines in mine,  I assume you will too. 

If you don't want to do the editing with xterm, you can also do it via thunar. Alt-F2 again, then run gksudo thunar. The files manager will then come up giving you root privileges, navigate to file, right click on it and edit it with mousepad. if you are worried about messing up, make a backup copy of the file before editing it. 

I believe you have to do a restart for the change to take effect. One way to do this of course is to click on the Xubuntu terminal and crash the program rather than  clicking the restart button.< grin>  But once you log in again, you should be set and the terminal will work the say it should. Some fellow figured this out a few months ago and I'm passing on his suggestions. Afaik, there are no negative effects on making this change.

eileen...

---

### Post by jamboyoungy on 2007-08-09
> **AnRa said:**
> It's a bug, a workaround is changing the color depth to 16.

Can't seem to see a color depth setting. Where is it hiding?

---

### Post by splintercellguy on 2007-08-09
See the post above. Basically you are editing /etc/X11/xorg.conf. Be sure to back up before making changes.

Press Alt-F2 and type: gksudo gedit /etc/X11/xorg.conf and follow the above instructions

After that, Ctrl-Alt-Backspace to restart the X server

---

### Post by jamboyoungy on 2007-08-09
Thanks for you help folks!

---

### Post by splintercellguy on 2007-08-09
Please mark your thread as solved to help others who may have a similar problem.

---

