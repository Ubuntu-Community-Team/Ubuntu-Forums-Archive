---
title: "Terminal Issue with XFCE"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Robert98374 on 2007-05-19
Hello again everyone :-),
Heres the issue that I'm having, i just installed just Xubuntu and i am trying to access the terminal. Every time i try to open the terminal it logs me out completely.. Anyone have any suggestions?

---

### Post by mahy on 2007-05-19
Press Alt+F2 and type 'xterm' into the newly emerged command line. Then post the results pls.

---

### Post by hyper_ch on 2007-05-19
what does syslog say?

---

### Post by Robert98374 on 2007-05-19
> **mahy said:**
> Press Alt+F2 and type 'xterm' into the newly emerged command line. Then post the results pls.

OK it brings up a terminal. So what exactly is xterm?

---

### Post by Robert98374 on 2007-05-19
> **hyper_ch said:**
> what does syslog say?

Syslog?

---

### Post by energiya on 2007-05-19
After you opened xterm, write [S]"terminal"[/S] "xfce-terminal" in it and execute. Post any errors. Check the syslog in /var/log or in the menu, find System Log (I forget)

---

### Post by jordanmthomas on 2007-05-19
^^ wouldn't he want to type 
```
xfce-terminal 
```
in his xterm?

and to the OP xterm is a terminal emulator, just like the one you're trying to get working.  It comes with Xorg and is kind of like "old faithful" of terminal emulators.

---

### Post by Robert98374 on 2007-05-19
it says command not found when i type in terminal. OK found the syslog how do you want me to post it?

---

### Post by Robert98374 on 2007-05-19
> **jordanmthomas said:**
> ^^ wouldn't he want to type 
```
xfce-terminal 
```
in his xterm?

and to the OP xterm is a terminal emulator, just like the one you're trying to get working.  It comes with Xorg and is kind of like "old faithful" of terminal emulators.

OK so its like (sorry for using windows terms) its like safe mode for terminal?

---

### Post by jordanmthomas on 2007-05-19
Sort of...I think you sort of get the idea at least.  It usually works and is pretty much unbreakable, so you can use it to fix other things...like Windows Safe Mode I suppose, but it's not crippled like safe mode is.

---

### Post by Robert98374 on 2007-05-19
Sorry just trying to take it to its lowest, simplest term

P.S. I was just lookng through my Add/remove list and i found that it terminal wasnt installed in the first place:-) thanks for the help

---

### Post by jordanmthomas on 2007-05-19
anyway, does anything happen when you type
```
xfce-terminal
``` into your xterm?

If it still logs you out you can probably run this to save any errors it gives you:
```
xfce-terminal >> termError
``` and then read the errors it gives (they'll be in a document called termError in your home folder)

---

### Post by hyper_ch on 2007-05-19
it's xfce4-terminal

---

