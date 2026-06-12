---
title: "How do I use a usb joystick as a mouse?"
date: 2012-07-19
forum: Assistive Technology &amp; Accessibility
---

### Post by MarjaE on 2012-07-19
I'm borrowing one to see if it reduces the strain on my arms and hands.

Unfortunately, it doesn't show up when I plug it in. [although ls /dev/input shows js0 when it is plugged in] Some of the info I've seen hasn't worked, some is several years old and uses jscalibrator, and some says it isn't an issue any more because the joysticks just work without any trouble.

[P.S. I'm using Gnome 2/Classic in 11.04 at this point. And my good arm is really hurting from having to twist around to use the keyboard or mouse.]

---

### Post by MarjaE on 2012-07-20
I was unable to install js2mouse, and although a friend of mine helped install qjoypad, I have been unable to get it to work.

---

### Post by MarjaE on 2012-07-21
It's working! The joystick will take some getting used to, but it's much less of a strain than the mouse. I'm not quite sure how to reproduce every step, but:

1. plug in the joystick.

2. look for it under ls /dev/input [in terminal] it should probably appear as js0 or something similar.

3. check if it's signalling anything using cat /dev/input/js0 [in terminal] it should produce gibberish as you move the joystick.

4. install joystick [which replaces jscalibrator] from the software center, and find and install qjoypad, this may take some doing from the tarball. you may want to bookmark the qjoypad documtation:

[http://qjoypad.sourceforge.net/doc/doc_index.html](http://qjoypad.sourceforge.net/doc/doc_index.html)

5. install the xorg joystick drivers from the software center, and find and install the appropriate drivers from here too [I'm not sure both sets of drivers are necessary, but I couldn't get it to work until installing both sets and restarting]:

[http://ubuntuforums.org/showthread.php?t=330607&highlight=joystick+interact](http://ubuntuforums.org/showthread.php?t=330607&highlight=joystick+interact)

if you have a usb joystick, you can skip the references to gameports and gameport drivers, and you can skip one line in the modules list edit.

6. restart, or wait until you've restarted.

7. run jscal [in terminal] to calibrate the joystick. I think the code is jscal /dev/input/js0 -c [in terminal] it should prompt you to move the joystick in various directions.

8. run qjoypad [in terminal or by looking in usr/local/bin - not in your personal directory] to start qjoypad. click on the top or bottom panel to open the settings. name your joystick, and start messing about with the settings. save once you've established ones that work for you.

9. Okay, it should be good to go!

---

