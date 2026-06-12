---
title: "How to close Putty but allow processes continue to run?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Fanatico on 2008-01-09
I run commands from my work XP computer in terminal window of my home Ubuntu computer with help of Putty via SSH.

I noticed that if I start any process from Putty command line (as root, with help of sudo -i) in my Ubuntu home computer and then close Putty window the process which was opened from Putty is terminated. My question: Is there any way to close Putty so that started processes on my Ubuntu home computer will not be terminated?

Thanks

---

### Post by geirha on 2008-01-09
You should look into screen. Not sure if the screen package is installed by default, so check that, and install if necessary. Then, when you log in with putty, type screen, which will give you a new shell (command line) looking quite similar to where you just were. Type your command, then hit CTRL+A+D to detatch, the program is now running in the background. Next time you log in, you can type "screen -r" to get that screen back, and see the results of the program you ran.

Run ```
man screen
``` to learn more about how to use screen.

---

### Post by Fanatico on 2008-01-13
Bump

---

### Post by geirha on 2008-01-13
Perhaps my previous post was hard to understand, so I found a tutorial on how to use screen here: [http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

Read it and try it.

---

