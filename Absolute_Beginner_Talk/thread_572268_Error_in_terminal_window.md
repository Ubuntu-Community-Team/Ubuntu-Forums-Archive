---
title: "Error in terminal window"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Pauliez on 2007-10-10
I am new to Linux and  just finished installing Ubuntu 7.04. I noticed that when I open a new terminal window I am seeing the following :  bash: /usr/bin/dircolors: cannot execute binary file. Does anyone have any suggestions what this might be?

---

### Post by phidia on 2007-10-10
Take a look at the thread [here]("http://ubuntuforums.org/showthread.php?t=1971&page=4") 
Hope that helps.

---

### Post by Pauliez on 2007-10-10
I checked and see where someone else saw the same thing, but there was no answer to the question.

---

### Post by nick_h on 2007-10-10
Have you checked to see if the file exists and is executable?

---

### Post by Pauliez on 2007-10-10
And what might the file be? I get this message when I open a terminal window.

---

### Post by nick_h on 2007-10-10
The file */usr/bin/dircolors* - I think it is used to define colours in commands like *ls*.

It will be run from the .bashrc script.

---

