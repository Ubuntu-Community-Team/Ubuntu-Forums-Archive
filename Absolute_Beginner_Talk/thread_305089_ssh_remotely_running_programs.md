---
title: "ssh remotely running programs"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by magquatre on 2006-11-22
Is there any way to ssh into an ubuntu machine and run a program that doesnt terminate when you end the ssh session?

thanks

---

### Post by bodhi.zazen on 2006-11-22
Try screen.

[list=number][*]ssh into your remote box.[*]type "screen"
[*]Then start the process you want from the command line.
[*]To "detach" type <Ctrl>-A <Ctrl>-D. This will "detach" your screen session but leave your processes running. You can now log out of the remote box.
[*]To resume the session, log on again and type "screen -r" This will "resume" your screen session, and you can see the output of your process.[/list]

[screen](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

---

### Post by IYY on 2006-11-22
I've always used "nohup". For example, to run **wget [www.google.com](www.google.com)** without it closing when I log out, I use
```

nohup wget www.google.com
```

---

### Post by bilange on 2006-11-22
Yup, screen is a nice program.

There's much more to read about it, try "Ctrl+A, ?" once you're in to see all the options available.

This way, you can also use a text-based IRC program remotely.

---

### Post by magquatre on 2006-11-22
thank you all very much

---

