---
title: "Help with screen key bindings"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by x1a4 on 2007-02-25
Hi,

I'm creating a kickass _.screenrc_ file but am having trouble finding help on how to assign two keybindings, perhaps someone here can assist me.  

1) When running *screen* the backspace key doesn't do anything so I want to bind it to do what the backspace key should do.  

2) I want to be able to bind Shift+PgUp/PgDown to scroll the buffer up/down.  I'm running a transparent terminal on the desktop without the toolbar, borders, menus, or scrollbar, and need to be able to scroll using the keyboard.  When not running *screen* Shift+PgUp/PgDown works, but I want to run *screen*.  

The *screen* man page is of no help.  

Thank you.

UPDATE: I figured out the solution but it only works in the Console and not the terminal.  

In _.screenrc_ I added

*bindkey -d -k kb stuff "\010"*

and the Backspace problem was solved, the Shift+PgUp/PgDn seems to work fine.  

When I run *screen* in the Xfce Terminal, however, neither the Backspace nor Shift+PgUp/PgDn work. 
In Multi GNOME Terminal Backspace works but not Shift+PgUp/PgDn, same in GNOME Terminal, PowerShell, RXvt and XTerm.  When I'm not running *screen* Shift+PgUp/PgDn works in all terminals as does Backspace.

---

### Post by n8bounds on 2007-02-25
Check this site out:

[http://www.dotfiles.com/index.php?cat_id=6](http://www.dotfiles.com/index.php?cat_id=6)

---

### Post by x1a4 on 2007-02-25
> **n8bounds said:**
> Check this site out:

[http://www.dotfiles.com/index.php?cat_id=6](http://www.dotfiles.com/index.php?cat_id=6)

Thanks but none of the screenrc files they have solves my problem.  I found one which seems to address the backspace issue but that only makes Backspace work like the Delete key--not good.  And none of them have a means to scroll.  Obviously there is a way since one of *screen*'s options is  the size of a scrollback buffer.

---

### Post by x1a4 on 2007-02-26
Okay, I solved the Backspace problem by telling Xfce Terminal that the Backspace key generates ^H but I still can't scroll using Shift+PgUp/PgDn.  I figured out how to scroll using *screen*'s method but it's awkward.  Any ideas?

---

### Post by notpip on 2007-04-14
entering screen scrollback is done by   ^A[  you can use vi style search and navigation.

---

