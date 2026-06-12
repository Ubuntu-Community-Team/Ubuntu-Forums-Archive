---
title: "Help the text when I right click on desktop turns into []'s"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by theone2punch on 2007-01-13
I was trying to upgrade firefox to 2.0 so i was following some random instructions on the net. I tried to run this in the terminal:

sudo apt-get install libstdc++5

(not i have no clue what that means anyway i was just following someone's tutorial)

I received an error and began searching for another way to do it, but noticed that the text on my desktop icons looks like those boxs when the character is not in the font set like [] but no space in between them.

When I right click on the desktop I get the same thing. 

How do I undo what I did?

---

### Post by MkfIbK7a on 2007-01-13
could you post the website with the instructions
that you followed?

---

### Post by SuperMike on 2007-01-13
You may want to back out your commands -- something's made either your video driver, GNOME, or your font driver unstable.

To find those commands, do:

$ gedit ~/.bash_history

and, to find out what was run for the 'root' account, do:

$ sudo gedit /root/.bash_history

Scroll from bottom to the top to see commands in reverse.

---

