---
title: "opening terminal from command line"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by thepopasmurf on 2007-12-22
How can I open the terminal using the command line commands
(in other words opening the terminal form the terminal)

---

### Post by jken146 on 2007-12-22
Do you mean you want to create a new terminal window?  Or do you want to run a new terminal window in an esisting terminal?

If the former is the case, then I think you can just press Ctrl+N, if it's the latter then type ```
gnome-terminal
```

---

### Post by shareMenaPeace on 2007-12-22
Maybe try

ALT F1 or ALT F2?

But maybe you mean something like 

start x  (ubuntu desktop - the X SERVER)

or 
x start

?

---

### Post by HermanAB on 2007-12-22
There are three ways that I know of:

IceWM may have ctrl-alt-t mapped to a terminal program - controlled by the IceWM 'keys' file.  

In KDE, you can configure the key shortcuts somewhere deep in the Control Centre wizard to do whatever you want.  

As a generic solution, you can use xbindkeys to bind any key to any program, for example to bind F12 to gnome-terminal or konsole.

'Hope that helps!

Herman

---

### Post by nowshining on 2007-12-22
it's 

startx

no spaces.

or in terminal right-click (if terminal) and select new tab, or new window/terminal.

---

### Post by thepopasmurf on 2007-12-22
> **jken146 said:**
> Do you mean you want to create a new terminal window?  Or do you want to run a new terminal window in an esisting terminal?
...... if it's the latter then type ```
gnome-terminal
```

Yes that's what I wanted

---

### Post by HermanAB on 2007-12-22
If you install xbindkeys, then you can add a file .xbindkeysrc in your home directory that looks like this:

"gnome-terminal"
  F12

Then modify .bash_profile and add this line to the bottom of it:

xbindkeys

Then to get it to work in the current session without having to log out/in run xbindkeys:

$ xbindkeys

Now if you press F12, a terminal will pop up.

Cheers,

Herman

---

