---
title: "Can't open Terminal"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by baharder on 2007-08-07
When I try to open a terminal it doesn't open and it seems to start up a new session instead. It sends me back to the login screen and I'm logged into a new session without the same applications I was running in the first one. Anyone run into this before?

I'm new to this so please be patient.

Thanks,
Bryan

---

### Post by Dr Small on 2007-08-07
I've never heard of this, but you could open run (ALT+F2) and type "gksudo gnome-terminal" and that will open the terminal as root. Just try that and see if the terminal will open that way.

Dr Small

---

### Post by canadianwriterman on 2007-08-07
Mmmm? How are you opening the terminal? By selecting it from the Applications menu at the top right-hand corner of your desktop?

---

### Post by baharder on 2007-08-07
I'm using the "Applications” -> “Accesories” -> “Terminal" to open it.

I tried the ALT-F2 suggestion as well. It prompted me for a password and then did nothing. I tried again and clicked the "run in a terminal" checkbox and then it started a new session.

I'm running Xubuntu 7.04 if that matters.

Thanks again

---

### Post by Inxsible on 2007-08-07
> **baharder said:**
> I'm using the "Applications” -> “Accesories” -> “Terminal" to open it.

I tried the ALT-F2 suggestion as well. It prompted me for a password and then did nothing. I tried again and clicked the "run in a terminal" checkbox and then it started a new session.

I'm running Xubuntu 7.04 if that matters.

Thanks again yup that matters, because you wouldn't have gnome-terminal installed 
try Alt + F2 and type in xfce-terminal

---

### Post by AlexenderReez on 2007-08-07
hm...after install gnome terminal,i suggest you to install nautilus-open-terminal ...so you can easily open terminal using right click of mouse :)

---

### Post by baharder on 2007-08-07
Thank you for the help.

I installed gnome-terminal and that seems to work.

I can't get xfce-terminal to work at all. Just opens a new session. I guess I'm not the only one that thinks that is weird!  :)

---

### Post by odbasta on 2007-08-07
> **AlexenderReez said:**
> hm...after install gnome terminal,i suggest you to install nautilus-open-terminal ...so you can easily open terminal using right click of mouse :)

...or [Tilda]("http://tilda.sourceforge.net/wiki/index.php/Main_Page"), to open like a game console with the tilde key.

---

### Post by rolypolycat on 2007-08-09
Hello!

I also ran into this problem running xubuntu. I also installed aterm and some other terminals, as well. They don't show up on my applications menu, however, so I don't know if they would work or not in xubuntu. How can I add them to my applications menu? Appfinder doesn't find them. And it can't find other apps I install with synaptic, either. If I add gnome-terminal, won't it add a bunch of gnome stuff? The other's didn't; that's why I chose them. I can't use them if I can't find them.
I'll be really grateful if someone can help find both my new terminals (unless these are also known to conflict with xubuntu, in which case I'll just remove them), and if someone can help me find my other missing apps. Thanks in advance!

---

### Post by vegipowrd on 2007-08-10
This is a well known bug.  I ran into it about a week ago and found this thread by needing the instructions to fix a second machine.  You have to change the /etc/X11/xorg.conf file.  There are two ways to do this.  

[http://ubuntuforums.org/showthread.php?t=521196&highlight=xubuntu+terminal+crash](http://ubuntuforums.org/showthread.php?t=521196&highlight=xubuntu+terminal+crash)

and

[http://ubuntuforums.org/showthread.php?t=417661](http://ubuntuforums.org/showthread.php?t=417661)

---

