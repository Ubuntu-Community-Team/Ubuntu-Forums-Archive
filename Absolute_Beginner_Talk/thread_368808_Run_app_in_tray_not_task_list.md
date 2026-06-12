---
title: "Run app in tray not task list?"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by x1a4 on 2007-02-23
Hi, 

On the command line if I want to fork a console app and run it as a daemon all I have to do is add an ampersand to the end of the command.  In Xfce, is there something similar I can do to run an application, either from the panel's command line applet or menu, to run in the system tray instead of the task list?  

Thank you.  

PS Obviously this doesn't apply to software which have a built-in provision  for running in the tray.

---

### Post by 23meg on 2007-02-23
You can do it with Alltray. It's in the repositories.

---

### Post by x1a4 on 2007-02-23
> **23meg said:**
> You can do it with Alltray. It's in the repositories.

No it's not--at least not on my system.  My sources.list entries are as follows: 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy multiverse universe main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

---

### Post by 23meg on 2007-02-23
I do see it in Universe here.```
$ apt-cache search alltray
alltray - Dock any application with no native tray icon
```

---

### Post by x1a4 on 2007-02-23
You probably have a repository I don't.  I try not to mess with 3rd party repositories.  Anyway, I googled *alltray* and yanked a copy from [http://alltray.sourceforge.net/](http://alltray.sourceforge.net/).

Thanks.

---

### Post by x1a4 on 2007-02-23
Hi,  

Alltray doesn't work the way I want.  Is there anything else?  

I need to be able to pass options to the command I'm running and alltray ignores them.

---

### Post by x1a4 on 2007-02-23
I found *kdocker* which seems to do the trick, albeit not 100% but well enough.

---

### Post by 23meg on 2007-02-23
> I need to be able to pass options to the command I'm running and alltray ignores them.What are you trying to run, and what's the exact command line you use?

---

### Post by x1a4 on 2007-02-23
> **23meg said:**
> What are you trying to run, and what's the exact command line you use?

Xfce Terminal

*xfce4-terminal --working-directory=/home/x1a4 --geometry=123x26+240+160 --hide-menubar --hide-borders --hide-toolbars*

When I run it with *alltray* all the options are ignored and the terminal opens in a regular window--not the way I want it.  While *alltray* does accept the --geometry option I can't pass the others to the terminal.  

BTW Is it possible to set an application to be ignored when clicking the 'Show Desktop' button, and if so how?  

Thanks.

---

### Post by 23meg on 2007-02-23
If you put the command in "double quotes", the options won't be ignored.

---

### Post by x1a4 on 2007-02-23
> **23meg said:**
> If you put the command in "double quotes", the options won't be ignored.

Already tried that, with both double and single quotes--no dice.

---

### Post by 23meg on 2007-02-23
The following works over here. ```
alltray "xfce4-terminal --geometry=123x26+240+160 --hide-menubar --hide-borders --hide-toolbars"
```

---

### Post by x1a4 on 2007-02-23
> **23meg said:**
> The following works over here. ```
alltray "xfce4-terminal --geometry=123x26+240+160 --hide-menubar --hide-borders --hide-toolbars"
```

What GUI are you using, because d it doesn't work on my end.  While it does dock the terminal in the system tray, it doesn't exclude it from the task list.  I can also still see the window decorations with the 'minimize' 'maximize' and 'close' buttons--must be an Xfce thing.    Anyway, thanks for your help, *kdocker*  is a good alternative and does get me what I want (for the most part).  

Thank you.  

BTW is there a way to exclude an application from being minimized when I click the 'Show Desktop' button on my panel?

---

### Post by 23meg on 2007-02-23
I'm using GNOME, and see no window decorations. To exclude it from the task list, use Alltray's -stask option. You can also remove window decorations with Alltray instead, using the -x option. Try this:```
alltray -x -stask "xfce4-terminal --working-directory=/home/x1a4 --geometry=123x26+240+160 --hide-menubar --hide-borders --hide-toolbars"
```

> BTW is there a way to exclude an application from being minimized when I click the 'Show Desktop' button on my panel?

Not that I know of, but you may be able to work around that with a hack using *wmctrl*. Check out its manual page, it's a nifty app.

---

### Post by x1a4 on 2007-02-23
It works!  Thank you. :D  I also figured out what I was doing wrong.  I followed the syntax in the *alltray* man page and put the *alltray* options after the command.  When I put the *alltray* options before the command then enclosed it in quotes it worked like a charm.  With the -x -s -stask options I can even see the terminal when I click the 'Show Desktop' button.  

Thank you.  O:)

---

### Post by 23meg on 2007-02-23
Good to know you got it working as you like. Check this out if you'd like to experiment a bit further: 

[http://www.ubuntuforums.org/showthread.php?t=81727](http://www.ubuntuforums.org/showthread.php?t=81727)

---

