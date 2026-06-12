---
title: "Where to install apps??"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by qiezi! on 2005-09-29
Hi

Have been using the Hoary Live CD, and was playing around with installing applications (Java and Azureus), I never realised installations could be so fun!! And it wasn't nearly as hard as I was expecting (I'm a Linux noob). I just wanted to ask where you experienced Linux users install your applications?? Mine where just on the desktop, but that would obviously get clustered. I'm thinking /usr/bin, but I just wanted a seasoned users opinion.

Thanks!!

---

### Post by aysiu on 2005-09-29
Well, installations are fun when you're using a live CD because it never damages your system! That said, I don't pick any directory to install apps. I just let Synaptic Package Manager take care of it. Read my sig for more details.

---

### Post by wmcbrine on 2005-09-30
If not using Synaptic or apt-get (which you should, whenever possible), the traditional locations are /usr/local/bin, or sometimes /opt for large packages with their own directory trees. /usr/bin is typically reserved for apps that are part of the distribution (which includes anything from Synaptic or apt-get).

These are guidelines; there are no rules, per se. But if you plan to run it from the command line, it ought to be in the $PATH.

---

### Post by qiezi! on 2005-09-30
Oo I think I get it... I was using apt-get just to get a feel for using the command line and b/c I couldn't find where Synaptic installed things... so was wondering... 
What do you mean by $PATH?? ie /usr/local/bin/whatever-the-app-is??

---

### Post by aysiu on 2005-09-30
[QUOTE=qiezi!]I couldn't find where Synaptic installed things... [/QUOTE] I was a bit disoriented by this, too, at first. Synaptic should create a menu item for your newly installed program. If not, you can create one, and the command is just the name of the program. For example, if you install Pioneers, the command to start it is just *pioneers*.

---

### Post by wmcbrine on 2005-09-30
[QUOTE=qiezi!]What do you mean by $PATH?? ie /usr/local/bin/whatever-the-app-is??[/QUOTE]That's a path, yes; but when I say $PATH, I mean the environment variable of that name. See, when you type a command without specifying the full path, the shell (bash) searches for it in the directories listed in $PATH. So if you want to be able to invoke a command that way, it needs to be in one of the directories listed there. (You can add to the list, of course.)

Example: You type "ls" to list a directory. If there were no $PATH, you'd have to type "/bin/ls" every time. But since "/bin" is in the $PATH, bash finds the ls program there without being told.

BTW, it works the same way in the Windows command shell, except that Windows adds an implicit "." (current directory) to the beginning of the PATH, and of course uses different separators.

---

### Post by qiezi! on 2005-09-30
[quote=wmcbrine]That's a path, yes; but when I say $PATH, I mean the environment variable of that name. See, when you type a command without specifying the full path, the shell (bash) searches for it in the directories listed in $PATH. So if you want to be able to invoke a command that way, it needs to be in one of the directories listed there. (You can add to the list, of course.)

Example: You type "ls" to list a directory. If there were no $PATH, you'd have to type "/bin/ls" every time. But since "/bin" is in the $PATH, bash finds the ls program there without being told.

BTW, it works the same way in the Windows command shell, except that Windows adds an implicit "." (current directory) to the beginning of the PATH, and of course uses different separators.[/quote] 
Ah I see, well that makes sense, and makes things easier when typing.  Cool!! Thanks!!

Thanks to aysiu too!!

---

