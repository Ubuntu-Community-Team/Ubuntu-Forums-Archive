---
title: "terminal man page"
date: 2013-07-10
forum: Any Other OS
---

### Post by linuxfan247 on 2013-07-10
I am trying learn the terminal. I learn to "sudo apt-get install update" so the updates are done faster. I really appreciate the persons blog that gave the tip I subscribed to his blog. Are there any pages/pdf's that show command line instructions. I am runnig Zorin OS 6.3 wich has been for the most an "working out of the box" experience.:)

---

### Post by dino99 on 2013-07-10
the links below might help you a lot

---

### Post by oldos2er on 2013-07-10
Moved to Other OS/Distro Support.

---

### Post by Buntu Bunny on 2013-07-10
There is a list of Command Line Resources at Ubuntu Community Resources [https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by The Cog on 2013-07-10
For the most part, the commands you enter into the command line are just the names of other programs that you are launching. So for instance, your command "sudo apt-get install update" is launching the program sudo (and telling it to launch the program apt-get). So you need to consult the manual to see what sudo is/does, and look at the manual for apt-get to see what apt-get is/does. Neither of these belong in "command line instructions" - they are programs in their own right. In the same way as you wouldn't expect details on adding and removing windows programs to be in a manual on how to use the mouse and keyboard.

The vast majority of these commands/programs have their own manual pages. You can look at these with (for instance) "man sudo" and "man apt-get". Use the up and down arrows, use "q" to quit, and use "/" followed by a search string and Enter, use "n" and "p" for the next and previous search result. For more details on how to use the man command/program, use "man man" (of course! It took me years  to figure that one out). You can of course google for more details on each of these programs - the man pages are really only a brief reference.

---

