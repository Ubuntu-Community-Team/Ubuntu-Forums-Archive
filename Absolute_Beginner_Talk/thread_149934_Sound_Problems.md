---
title: "Sound Problems"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by bpazolli on 2006-03-25
This isn't your average day my sound card dosn't work problem. I have an iMac 333 and for a few games the sound dosn't work when I launch them from the menu, but when I launch them from the terminal it works perfectly. Other applications sound works when launched from the menu and general GUI sounds work as well. The games I have noticed it with is Frozen Bubble and Nibbles. It is strange because it was my understanding that when you clicked a game in a menu it was just like a shortcut typing in the command into the command line.

Thank You,
Ben Pazolli

---

### Post by Pragmatist on 2006-03-25
What happens if you use a launcher?  Right-click the panel, choose 'application launcher' and pick the program via the 'wizard' from your menu.  Then right-click on the newly-created launcher and select 'properties'.  Look for the 'command' line and around there there should be a checkbox for "run in a terminal".  Check the checkbox, and then when your done, click the launcher and see if the sound works.

---

### Post by Pragmatist on 2006-03-25
Nevermind.  You can do it for menu entries as well.  Just open the menu editor.  You can do it from a terminal by typing:
```
smeg
```
find your program, double-click on the entry in the left panel window and you'll see a line with the command to run the program and you'll also see a checkbox for "run in terminal" check it and everything SHOULD work :)

---

### Post by bpazolli on 2006-03-25
I did what you said by selecting run in terminal. And when frozen bubble works I get this message open "*/dev/sequencer: No such file or directory*" and when it dosn't work I get "*Warning: can't initialize sound (reason: No available audio device).*". A guess is maybe I havn't installed it completly properly.

Any Help appreciated,
Ben Pazolli

---

