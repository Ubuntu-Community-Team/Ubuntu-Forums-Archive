---
title: "how to open a terminal using command line"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by pranjalsaxena on 2008-04-13
Hi !
please help me out.I want to open a terminal from command line(like opening a terminal  from another terminal).Is there any such command .

Thanking you in advance

---

### Post by t1n0m3n on 2008-04-13
gnome-terminal

---

### Post by forrestcupp on 2008-04-13
You can also press alt+F2 and type that command in the Run Application dialog.

---

### Post by t1n0m3n on 2008-04-13
Or use CTRL+Shift+N while the 1st terminal is focused.  :)

---

### Post by t1n0m3n on 2008-04-13
Or click the Deskbar applet and type the command in there.  :guitar:

---

### Post by lswest on 2008-04-13
The command depends on your desktop environment:

for GNOME:
```
gnome-terminal
```

for KDE:
```
konsole
```

for XFCE:
```
xterm
```

---

### Post by goiggles on 2008-04-13
If you have konsole installed you can also use the command konsole or if you want to type less and don't mind not having extra features you can use xterm too.

you might need to type an & after the commands to run them in the background so you can have the original terminal back.also fyi you can set a keyboard shortcut for the terminal under system>preferences>keyboard shortcuts

---

### Post by pranjalsaxena on 2008-04-13
Thank you everybody for your help
gnome-terminal worked fine for my job on ubuntu .Is there any platform independent solution also if so please tell

---

### Post by pranjalsaxena on 2008-04-13
Sorry I did not specified clearly in my last post actually I wanted to ask whether there is solution which does not depend whether it is KDE or GNOME??

---

### Post by PeterJS on 2008-04-13
An xterm is an xterm, it runs everywhere, but isn't pretty or well integrated anywhere. Ubuntu provides a x-terminal-emulator, that is a symlink to the alternatives system which is itself a symlink to the actual terminal program.

---

### Post by Hendrixski on 2008-04-13
If you need to have multiple command lines going at once... there's a few options:

GNU Screen

GNU Screen is a program to run virtual commandlines on top of each other.  And it's got tons and tons of functionality.

If you just want to have a couple of commandlines open at once, and you're in GNOME's terminal, just hit SHIFT+CTRL+T and you get a new tab... just like in firefox when you hit CTRL+T

And you already have 9 commandlines. well 8,... if you hit CTRL+ALT+F1 you get a terminal... no windows or anything just terminal.  do some stuff there and if you need another one just hit ALT+F2  and so on... until you try CTRL+ALT+F7 which returns you to your visual session.

cool huh?

---

### Post by Hendrixski on 2008-04-13
Oh yeah, and if you never entered into a graphical session (like if you're in the safe mode or whatever it's called) you can run xinit -C gnome-terminal and it opens just that terminal, no other windows.

You can do that with any program.  

I think it's -C... I could be wrong.  read the xinit man page '-)

---

### Post by stuart brogan on 2008-04-13
I would like to add that if you put an ampersand & character after the command you can keep that terminal going while opening up the next one.

For instance xterm &
dclock &
etc.

---

### Post by pranjalsaxena on 2008-04-13
and how we will send a command to xterm as in "gnome-terminal --command  ........"

---

### Post by ozzyprv on 2008-04-27
> **Hendrixski said:**
> If you need to have multiple command lines going at once... there's a few options:

GNU Screen

GNU Screen is a program to run virtual commandlines on top of each other.  And it's got tons and tons of functionality.

If you just want to have a couple of commandlines open at once, and you're in GNOME's terminal, just hit SHIFT+CTRL+T and you get a new tab... just like in firefox when you hit CTRL+T

And you already have 9 commandlines. well 8,... if you hit CTRL+ALT+F1 you get a terminal... no windows or anything just terminal.  do some stuff there and if you need another one just hit ALT+F2  and so on... until you try CTRL+ALT+F7 which returns you to your visual session.

cool huh?

Intersting, I have to hot CTRL+ALT+F9 to go back to the visual session.

---

### Post by AaronMT on 2008-04-27
For years, I have been using the keyboard command, "Ctrl-Alt-X" to open a terminal. Binding this shortcut is one of the first things I do on a new GNU/Linux install. You can setup this shortcut in Ubuntu

```
System -> Preferences -> Keyboard Shortcuts -> (Desktop : Open a Terminal Window)
``` :KS

---

