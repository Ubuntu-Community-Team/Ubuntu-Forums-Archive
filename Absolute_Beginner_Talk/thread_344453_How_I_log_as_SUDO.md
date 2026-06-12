---
title: "How I log as SUDO"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by rictus007 on 2007-01-22
Hi

I need to put two files on this folder /usr/share/firefox/searchplugins

I know that I need to log as Sudo in oder to do that, because otherwise something about the permissions that I have don't allow me to simply copy and paste the files on this folder.

How I log as Sudo in Order to gain permission to put two files on this folder?  BTW There's any special way to do that or just simply "copy and paste"?

---

### Post by meng on 2007-01-22
You don't log in as sudo, you just put sudo at the front of the command
e.g.
sudo mv [source] [destination]
(enter your user password when prompted)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bachstelze on 2007-01-22
In UNIX-like systems, the "super user" is called "root". "sudo" is just a command that will let you run other commands as though you were root. Which is what you will be using there. Open up a terminal, use cd to browse to the directory where those files are located in and do :

```
cudo cp file1 file2 /usr/share/firefox/searchplugins
```

Voilà :)

---

### Post by Icemanyurt on 2007-01-22
One of the things that might work is to change the permissions of the folder by right clicking on the folder and opening properties.  Then going to the permissions tab and changing the read/write access settings...

*Edit: Or what said.  That might be safer and is more then likely more correct*

---

### Post by Bachstelze on 2007-01-22
For this to work, it requires to have Nautilus (or whatever file manager) running as root, which is IMO a *very* bad idea.

---

### Post by deanlinkous on 2007-01-22
sudo nautilus

---

### Post by aysiu on 2007-01-22
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) will help you.

---

### Post by Shatrat on 2007-01-22
> **Icemanyurt said:**
> One of the things that might work is to change the permissions of the folder by right clicking on the folder and opening properties.  Then going to the permissions tab and changing the read/write access settings...

you'd have to be root to do that to a folder that isnt yours though, so either way you need sudo

---

### Post by Icemanyurt on 2007-01-22
Oh fair enough, thanks

---

### Post by aysiu on 2007-01-22
> **deanlinkous said:**
> sudo nautilus Or, better yet, ```
gksudo nautilus
```

> **Icemanyurt said:**
> One of the things that might work is to change the permissions of the folder by right clicking on the folder and opening properties.  Then going to the permissions tab and changing the read/write access settings...

*Edit: Or what said.  That might be safer and is more then likely more correct* Yes, changing permissions on system folders is a quick way to break your system.

> **HymnToLife said:**
> For this to work, it requires to have Nautilus (or whatever file manager) running as root, which is IMO a *very* bad idea. Why is Nautilus as root such a bad idea? I've done more bad things by accident with the terminal than with Nautilus as root.

---

### Post by Buck2348 on 2007-01-22
If you'd rather do the file moving/copying by dragging and dropping instead of terminal commands, you can type ```
gksudo nautilus 
```in a terminal (Applications -> Accessories -> Terminal).  In the window that opens you can move around and operate with the permissions of the superuser.

---

### Post by Atomic Dog on 2007-01-22
Consider using sudo like using the jedi mind trick.

User@UbuntuLaptop:~$ Sudo these aren't the droids you're looking for

---

### Post by Bachstelze on 2007-01-22
I just don't trust anything that make copy/paste so easy and thoughtless. I'm pretty sure that doing a drag-and-drop by mistake is a quite common thing. In a terminal, you have to type it all, so the chances of doing something without thinking about it are reduced. But then again, it's just my opinion about it, I know that if I had the habit of running Konqueror as root, I'd certainly break something sooner or later.

---

### Post by rictus007 on 2007-01-22
Thanks Everyone...It works!!!

---

### Post by Icemanyurt on 2007-01-22
How does gksudo differ from sudo?

---

### Post by aysiu on 2007-01-22
> **HymnToLife said:**
> I just don't trust anything that make copy/paste so easy and thoughtless. I'm pretty sure that doing a drag-and-drop by mistake is a quite common thing. In a terminal, you have to type it all, so the chances of doing something without thinking about it are reduced. But then again, it's just my opinion about it, I know that if I had the habit of running Konqueror as root, I'd certainly break something sooner or later. I think it really depends on how the user thinks. The way I think, the terminal is far more dangerous. For more details, read [this thread](http://ubuntuforums.org/showthread.php?t=332453). Since I think phonetically, *rm* sounds a lot like *mv* to me. And *rm* permanently deletes, whereas even root Nautilus defaults to *move to trash* instead of a hard delete.

> **Icemanyurt said:**
> How does gksudo differ from sudo? Read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by deanlinkous on 2007-01-22
in a terminal a mistake can have severe consequences, not so much in the file manager IMO

I mean you may get the syntax wrong or just not know what something is going to do in a terminal whereas with the file manager you KNOW what you are copy/paste and if you screw up it was just stupidity.... :D

---

### Post by Atomic Dog on 2007-01-22
> **deanlinkous said:**
> in a terminal a mistake can have severe consequences, not so much in the file manager IMO

I mean you may get the syntax wrong or just not know what something is going to do in a terminal whereas with the file manager you KNOW what you are copy/paste and if you screw up it was just stupidity.... :D

Yes.  I have made one too many mistakes using commands like rm.  I do the old gksudo nautilus when I have to remove folders/files that are owned by root.

---

### Post by Bachstelze on 2007-01-22
I think it's also stupidity to type anything in the root terminal when you don't know what you are doing. Running a file manager as root is not a bad thing in itself, but you need do be extra careful. Just imagine you have your Nautilus running as root and you're just moving you mouse in it. Now your little sister's cat jumps on your hand, you do a drag-and-drop, broken system. It could have happened to me several times if I had this habit :p

---

### Post by Atomic Dog on 2007-01-23
> **HymnToLife said:**
> I think it's also stupidity to type anything in the root terminal when you don't know what you are doing. Running a file manager as root is not a bad thing in itself, but you need do be extra careful. Just imagine you have your Nautilus running as root and you're just moving you mouse in it. Now your little sister's cat jumps on your hand, you do a drag-and-drop, broken system. It could have happened to me several times if I had this habit :p 

Yea, but thankfully it is fairly rare to need to open nautilus as root.  I would say I most often use gksudo gedit to edit a conf file here, grub file there and I always make a backup before starting. 

...and my cats would not DARE jump on the laptop.

---

### Post by misha680 on 2007-01-23
> **Icemanyurt said:**
> How does gksudo differ from sudo?

Gksudo pops up a dialog asking for your password, so it will work if you use ALT-F2 to launch a command. sudo will ask for your password from standard input (i.e., in the terminal) so you can't use it in ALT-F2 or for a shortcut (can't remember what they are called in Ubuntu right now, doh).

misha

---

