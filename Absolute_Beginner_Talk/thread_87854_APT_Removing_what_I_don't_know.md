---
title: "APT: Removing what I don't know"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by ramdisc on 2005-11-09
I am trying to remove some useless programmes.  But the problem is, I don't know the name it goes by in CLI.  How do I find the CLI of a programme?  Such as Bluetooth that I don't use.  I want to uninstall it.  But it doesn't correspond to "bluetooth" in APT.

How do I know the programme CLI's name?

---

### Post by johannes on 2005-11-09
I'm sure there is a list of them somewhere, but you can find out their CLI names by using the Applications > System Tools > Applications Menu Editor. Just right click a program, choose Properties and you'll see it in the Command box. That is if you are using Gnome of course, otherwise I don't know...

---

### Post by gruepig on 2005-11-09
Yes, this will tell you the name of the program you are running.  In many cases the program name will correspond to the package name.  If not, you'll still need to find the package associated with that program.  There's probably a way to do this in aptitude (though I don't know how off-hand).  From the command-line, you may be able to identify the package name by running 'dpkg -S <program>'.

---

### Post by Qrk on 2005-11-09
You can also search synaptic for they installed program (use the installed filter) and uninstall it from there.

---

