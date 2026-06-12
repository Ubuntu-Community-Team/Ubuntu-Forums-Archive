---
title: "Need ehlp installing .sh program"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by jfank on 2008-02-25
A friend of mine gave me a copy of cross over 5.0.3 pro, and I know it works perfectly because he has it in his computer.  Now the problem that I'm having is it is a .sh file, and I have never heard that file type before.  I'm trying to get it to install on Kubuntu 7.10, but having zero luck.  Can some please give me a hand with this.  thank you, and below I will give the exact file name.

install-crossover-pro-5.0.3.sh

Thank you for the help.

---

### Post by oedha on 2008-02-25
have you double click it ? and run from terminal ?

---

### Post by Arkenzor on 2008-02-25
First, make sure it is marked as executable. You can do this either by right-clicking it and choosing properties, or in the command-line with "chmod +x *filename*". Once that's done you should be able to run it by double-clicking it.

If nothing happens when you run it, then it probably means it needs to be run in a terminal. There may be an option for this in the right-click menu (I don't know which DE you're using, and don't remember which has what either anyway). If not, open the terminal yourself, cd to the right directory, and run your file with "./*filename*". It may (read: will probably) complain about not having root privileges, so instead use "sudo ./*filename*".



Also, I hope you trust that friend. Installing software through executable files is generally not advised.

That's it

---

### Post by jfank on 2008-02-25
I think I'm just going to go ahead and just buy a version of the software.  I tried to get it to run, but the software won't install.  I know it works on my friends computer, but he is using  Fedora Core 8.  All the software he has givin me works great, but this one just won't work at all.  If I can get it to work then I'll post on here about it, but like I said I will probably just buy the software from codeweavers to make it easier on myself.  Thank you for the help though.

---

### Post by fenian on 2008-02-26
Open a terminal and navigate to the directory the file is in ,if its in your home folder you don't have to do any navigating,if it's ay on your desktop you would need to enter this...

> cd ~/Desktop

then enter...

> sh install-crossover-pro-5.0.3.sh

---

### Post by wirelessmonkey on 2008-02-26
Crossover Pro requires a valid serial anyway, and is available as an rpm, a deb, and an ebuild, among others.  If he&#347; running fedora, it&#347; probably not gonna run on your ubuntu box.

---

