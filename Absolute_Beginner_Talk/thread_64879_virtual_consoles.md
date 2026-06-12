---
title: "virtual consoles?"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by kook44 on 2005-09-12
Hi-
I thout that all linux distros we able to switch between virtual consoles by keying Alt+F[1-7].

I am not able to do this in ubuntu.  Is this not enabled by default on ubuntu?

(I have also tried Ctrl+Alt+F[1-7] and Ctrl+F[1-7] - still unable to do it)

---

### Post by red_Marvin on 2005-09-12
Just a silly question: When you say F[1-7] you do mean the F# keys at the top
of the keyboard net F+number, right?

---

### Post by kook44 on 2005-09-12
[QUOTE=red_Marvin]Just a silly question: When you say F[1-7] you do mean the F# keys at the top[/QUOTE] 

haha. yes.  The "function" keys at the top of the keyboard.

---

### Post by ranf on 2005-09-12
[QUOTE=kook44]
(I have also tried Ctrl+Alt+F[1-7] and Ctrl+F[1-7] - still unable to do it)[/QUOTE]
Ctrl+Alt+F[1-6] when you're in X.
Alt+F[1-7] when on one of the consoles (where Alt+F7 is the X display).

Dunno why that should not work for you. You haven't edited your /etc/inittab, have you?

---

### Post by kook44 on 2005-09-12
[QUOTE=ranf]You haven't edited your /etc/inittab, have you?[/QUOTE] 
Nope.

I've tried both in a terminal window running under GNOME, and in a remote ssh session (putty).

I get the following output:

Alt+F1:  [11~
Alt+F2:  [12~
Alt+F3:  [13~
Alt+F4:  nothing
Alt+F5:  nothing
Alt+F6:  [17~
Alt+F7:  [18~
Alt+F8:  [19~
Alt+F9:  [20~
Alt+F10:  [21~
Alt+F11:  [23~
Alt+F12:  [24~

 ](*,)

---

### Post by ranf on 2005-09-12
[QUOTE=kook44]
I've tried both in a terminal window running under GNOME,
[/QUOTE]
Do you just want tho have more terminals? Ctrl+Shft+T creates a new tab ingGnome-terminal. Ctrl+PgUp Ctrl+PgDn switches thru them.
[QUOTE=kook44]
 and in a remote ssh session (putty).
[/QUOTE]
virtual consoles (Ctrl+Alt+F1) don't work over ssh. Try "man screen". (hint: screen -R, then Ctrl+A  c for a new screen. Ctrl+A  <Space> switches thru)

---

### Post by jimcooncat on 2005-09-12
I agree -- screen is wonderful when working with PuTTy. Do the "screen -R" to get it going like ranf says, and "Ctrl-A ?" will give you quick help. 

If you need to transfer files, check out WinSCP. It will import your PuTTy accounts. [http://winscp.net/eng/docs/introduction](http://winscp.net/eng/docs/introduction)

---

### Post by kook44 on 2005-09-12
[QUOTE=ranf]virtual consoles (Ctrl+Alt+F1) don't work over ssh. Try "man screen". (hint: screen -R, then Ctrl+A c for a new screen. Ctrl+A <Space> switches thru)[/QUOTE]
yep, that's it.  Thanks!

---

