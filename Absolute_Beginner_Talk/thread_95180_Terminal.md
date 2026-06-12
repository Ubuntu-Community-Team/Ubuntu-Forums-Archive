---
title: "Terminal"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by ivanroboto on 2005-11-25
My Terminal doesnt work.
Whenever i try launching it it says:

Cannot launch entry

Details: Failed to execute child process "Terminal" (No such file or directory)

---

### Post by Xian on 2005-11-25
You are using an incorrect launcher command.
Try the following:

gnome-terminal --working-directory=%f

---

### Post by ivanroboto on 2005-11-25
where do i type in these commands?? I thought thats waht terminal was for. 
Sorry im very very new to linux

---

### Post by ivanroboto on 2005-11-25
sorry i realize my mistake. 
wasnt looking in the right place.

---

### Post by durand on 2006-01-20
Use CTRL + ALT + F1 to enter a terminal. Use this info from another thread:
[QUOTE=thinhlegolas]It's simply because /usr/local/RealPlayer/realplay is not in the path

You should do this

export PATH=$PATH:/usr/local/RealPlayer/

or

ln -s /usr/local/RealPlayer/realplay /usr/bin[/QUOTE]
 Change the ```
export PATH=$PATH:/usr/local/RealPlayer/
``` to ```
export PATH=$PATH:/usr/bin/
``` and hopefully:rolleyes: it should let u run the terminal using a shortcut or the menu.

BTW: To get out of the black terminal, Use CTRL + ALT + F7
You might need to logout and login back again or restart ur computer.

---

