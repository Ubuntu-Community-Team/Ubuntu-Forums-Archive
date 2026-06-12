---
title: "how do i go to a directory"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by cbivins on 2007-08-08
I know this sounds really stupid, but i'm running a howto to set up my wireless card and i am doing fine until i get to the step where i am attempting to complile the Ndiswrapper program. it tells me "In a terminal, go to the directory where you extracted ndiswrapper and execute the following:" I know about the terminal, and i know where i extracted the ndiswrapper, but what does it mean to go to a directory in a terminal? Thank you to anyone who can help me out with this beginner question.

---

### Post by bodhi.zazen on 2007-08-08
cd /directory

Command line tips:
	[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
	[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)
	[http://www.justlinux.com/nhf/Command_Reference](http://www.justlinux.com/nhf/Command_Reference)
	[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by por100pre1 on 2007-08-08
> **cbivins said:**
> I know this sounds really stupid, but i'm running a howto to set up my wireless card and i am doing fine until i get to the step where i am attempting to complile the Ndiswrapper program. it tells me "In a terminal, go to the directory where you extracted ndiswrapper and execute the following:" I know about the terminal, and i know where i extracted the ndiswrapper, but what does it mean to go to a directory in a terminal? Thank you to anyone who can help me out with this beginner question.

Just write in a "terminal" window:

```
cd 
```(with an space after "cd")

and then drag and drop the folder into the terminal window.

(This only works in X, terminal windows are actually terminal emulators. :) )

---

### Post by solar george on 2007-08-08
Could you not use the ndiswrapper program that is in the repositories?

```
sudo aptitude install ndiswrapper
```

---

### Post by cbivins on 2007-08-08
thank you very much. i had been stuck for awhile on that. And i have no idea why the ndiswrapper program needed to be removed and then reinstalled, but that's what the howto said, and it's working now.

---

### Post by feistyfirsttimer on 2007-08-08
> I know about the terminal, and i know where i extracted the ndiswrapper, but what does it mean to go to a directory in a terminal?

This is something that's bugged me for a while now.  In Unix, they're called **directories**, as they are in Linux in the BASH shell.  Hence the terminal command **cd**, meaning **change directory**.

But when you get into the GUI, eg. Gnome, they're suddenly called **folders**, and are represented by a little picture of a folder.  Just like in Windows...

Why oh why did the GUI developers decide to rename directories as folders?  Was it a deliberate ploy to cater for MS Windows refugees?  What was the reason for this seemingly useless change in terminology?  It isn't particularly useful, you know - as I already said, users who are used to Gnome are gonna be lost whenever instructions mention directories.

---

