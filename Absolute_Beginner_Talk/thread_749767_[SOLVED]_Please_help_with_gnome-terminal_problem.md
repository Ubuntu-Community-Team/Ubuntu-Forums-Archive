---
title: "[SOLVED] Please help with gnome-terminal problem"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2008-04-08
I am running a fully updated Ubuntu Hardy Heron Beta. I was trying to get the terminal to load in a 140x25 resolution by default. So I went into: Edit -> Current Profile -> Title and Command. I then clicked on "Run a custom command instead of my shell." I then typed 'g' into the "Custom command:" line and the terminal froze, and then crashed.
I also just tried to put "gnome-terminal --geometry=140x25" into gedit and then paste it into the Custom command. When I then try and open a terminal, it will do one of two things:
 1) It will open one with the default size, and then will continue to open new terminals with the size I want, but it will close the other first. So they are unusable.
 2) It will open one with the default size, and then will continue to open new terminals with the size I want, but it will not close any.

I reported the bug [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/214325"), but I have no terminal I can use. Can anyone tell me how to reset the gnome-terminal to default settings? Please

---

### Post by DariusS on 2008-04-08
possible work-around might be to install another CLI??

---

### Post by spiderbatdad on 2008-04-08
try it like this...right click on the terminal icon and select properties...at the end of the command line add geometry=140x25
you may also need to specify x and y...like --geometry=140x25+0+0

Hmmm? seems to be a bug.

---

### Post by slughappy1 on 2008-04-09
I already did that. But I guess I should say something else. I just installed [Gnome-Do]("http://do.davebsd.com/") When I try and load the terminal through it, it would load the terminal in the standard size. When I load the terminal using Applications -> Accessories -> Terminal and with Gnome-Do it freaks out.

Is there a way to reset the gnome-terminal to default settings? Maybe by logging in using Ctrl + Alt + F2? Or something?

---

### Post by slughappy1 on 2008-04-09
Ok, I was able to "fix" the problem. When I tried to load the terminal and it kept loading tons of them, I right clicked on the menu bar and said always on top. Then I was able to delete the Custom command.

---

