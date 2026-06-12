---
title: "Help!!!!"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by grayfox2721 on 2008-04-02
Well, I don't need help, that bad. But I'm new to linux (been using for a week) I've adapted well to linux....however. I have a problem with installing files. I know the code on how to do so but I cant find the files, exe and, and don't know how to run it!!! I've spanned the internet all this week and nothing has helped. I sudo apt-get install gkrellm but I don't know where it is or how to get it to run Help please. 

-Much appreciated

---

### Post by xelapond on 2008-04-02
There are no .exe files in Linux.  Try running gkrellm from the command line.

If this works you can go into the menu editor and make it an icon in the menu.

Hope that helps!

---

### Post by ghost_ryder35 on 2008-04-02
go to the terminal and type
```
gkrellm
```
should start right up if it was installed correctly

---

### Post by Crafty Kisses on 2008-04-02
After you install gkrellm do the following:
Open up Terminal and type: ```
gkrellm
``` See if that does it.

---

### Post by grayfox2721 on 2008-04-02
yep worked....no way, thanks man

---

### Post by ghost_ryder35 on 2008-04-02
GREAT!  You should mark this thread as solved now
Go to "Thread Tools" at the top of the page and click on "Solved"

---

### Post by grayfox2721 on 2008-04-02
sorry, nother noob question. (sorry) how do I install themes now??, and how do I get it to go when i start up my pc, and so it doesn't shutdown gkrellm when I close the terminal

---

### Post by Crafty Kisses on 2008-04-02
> **grayfox2721 said:**
> sorry, nother noob question. (sorry) how do I install themes now?? lol

You'd go to your 'Theme Manager" and there should be an option called "Install", click that and click on the theme you want installed, and that should do the trick.

---

### Post by Mogurijin on 2008-04-02
Anytime you run a program from the terminal closing said terminal will terminate the program that you were running. Try looking for your program in the main menu.

---

### Post by louieb on 2008-04-02
more than one way.
start gkrellm by pressing Alt+F2 to bring up the run dialog. and entering gkrellm there.
or go to System>Preferences>Session and add it as a startup program.

or in the terminal ```
gkrellm &
```then to close the terminal window and leave gkrellm running type ```
exit
```

---

