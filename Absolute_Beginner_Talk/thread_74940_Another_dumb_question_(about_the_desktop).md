---
title: "Another dumb question (about the desktop)"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by gandalf458 on 2005-10-13
I assume the desktop is there to populate with shortcuts to my favourite applications just like Windows, but I have a problem with terminology and with finding things in Linux. I'm on Hoary 5.04.

How do I create a shortcut? Is it create launcher?

If so, where do I find the command? I click on Browse but where do I find the executable? Say I want to create a shortcut to the game mahjongg?

Thanks

---

### Post by Jussi Kukkonen on 2005-10-13
[QUOTE=gandalf458]Say I want to create a shortcut to the game mahjongg?[/QUOTE]


Easy way: Open *Applications/Games*, right-click Mahjongg, select *Add this launcher to desktop*.

A little less easy: If you didn't have it in the menus in the first place, you'd have to create the launcher (*Create Launcher*, surprisingly). If the executable is in your path (as usual) you can just put *mahjongg* as command, otherwise you'd have to find it first: ```
locate mahjongg
``` from the command line will tell you the correct command (in this case */usr/games/mahjongg*).

---

### Post by gandalf458 on 2005-10-13
Many thanks.

[QUOTE=Jussi Kukkonen]Easy way: Open *Applications/Games*, right-click Mahjongg, select *Add this launcher to desktop*.[/QUOTE]

I don't have *Add this launcher to desktop* only *Add this launcher to panel* or *Add this as drawer to panel* or *Add this as menu to panel*. 

The second way seems the only I can find to put it on the desktop. And that works fine.

Cheers

---

### Post by patrick295767 on 2005-10-13
[QUOTE=gandalf458]I assume the desktop is there to populate with shortcuts to my favourite applications just like Windows, but I have a problem with terminology and with finding things in Linux. I'm on Hoary 5.04.

How do I create a shortcut? Is it create launcher?

If so, where do I find the command? I click on Browse but where do I find the executable? Say I want to create a shortcut to the game mahjongg?

Thanks[/QUOTE]
   
I am a damn newbie!! and my way to do is very easy :
I installed rox-filer 
xterm : then enter rox & rox &
   
than when u take a file and do drag and drop to the desired location :
a tiny menu appears and u can choose LINK (shortcut) !!!!!

That's easiest way. 
Rox-filer is like explorer in Windows (but for my oldest pc's (fast)).

Btw, as u are newbie, u can use msn messenger, I'll reply you, if you have more questions... cos alone I would never be able to use Linux 'cos it's tooo difficult.

Courage !

Pat

---

### Post by Wolki on 2005-10-13
You can add the icon to the panel, then drag&drop it to the desktop.

---

### Post by bdash on 2005-10-13
You can simply drag'n'drop from the Application menu to the Desktop.

---

### Post by gandalf458 on 2005-10-13
Ah, yes dragon drop (either way) is a lot easier - and I get the right icon for the app, which I didn't when using create launcher. Cheers

---

### Post by gandalf458 on 2005-10-13
[QUOTE=patrick295767]I installed rox-filer 
xterm : then enter rox & rox &[/QUOTE]

You're way ahead of me, Pat!

I'm having enough fun with the software already installed without downloading any more! ;)

Getting used to Linux and Ubuntu is a sparetime project while I continue to use my Windows m/c to earn a living...

---

### Post by Wolki on 2005-10-13
[QUOTE=patrick295767]
than when u take a file and do drag and drop to the desired location :
a tiny menu appears and u can choose LINK (shortcut) !!!!!
[/QUOTE]

You can do the same with nautilus. Just drag with the middle mouse button to get such a menu. Or drag with the left button and hold <shift>+<ctrl> to link directly.

ROX is pretty awesome though. Be sure to visit [http://rox.sf.net](http://rox.sf.net) to learn more about this awesome desktop environment :)

---

