---
title: "Root Problem"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by Khamero on 2005-12-09
Hello! 
I am quite new to ubuntu, and I have a slight problem. 
The root password dosent work in the GUI. 
Neither in KDE or GNOME. I try to start, for instance, synaptic, I type in the password, but it says its incorrect. So I open the terminal, use su - to get root access, type in the password (the very same one, yes) and type "DISPLAY=:0 synaptic", and it works. But problem is that I have other programs that I do not know the commands for, and the DISPLAY command has stopped working too. Ie heard alot of sudo, but I do prefer su -, and i do not know how to implement either one in the GUI.

If anyone whould please help, it whould be much appretiated.

---

### Post by Rackerz on 2005-12-09
In Ubuntu and Kubuntu the root user is by default turned off. Look on this page for more info on how to enable it. [https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin](https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin)

Go down to the bit were it says 'Enabling the root account' thats were you want to start reading from. Make sure to go all the way to the bottom, following those instructions if you want the root user enabled and the GUI login too. 

It cannot be stressed enough though, do not use the root user as your default user.

---

### Post by cwaldbieser on 2005-12-09
[QUOTE=Khamero]Hello! 
I am quite new to ubuntu, and I have a slight problem. 
The root password dosent work in the GUI. 
Neither in KDE or GNOME. I try to start, for instance, synaptic, I type in the password, but it says its incorrect. So I open the terminal, use su - to get root access, type in the password (the very same one, yes) and type "DISPLAY=:0 synaptic", and it works. But problem is that I have other programs that I do not know the commands for, and the DISPLAY command has stopped working too. Ie heard alot of sudo, but I do prefer su -, and i do not know how to implement either one in the GUI.

If anyone whould please help, it whould be much appretiated.[/QUOTE]

In the GUI, you can use gksudo.

---

