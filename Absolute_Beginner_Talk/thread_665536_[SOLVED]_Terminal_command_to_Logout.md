---
title: "[SOLVED] Terminal command to Logout?"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-01-12
To logout I click 'shutdown' icon, then choose 'Log Out'.

What is the command for this in gnome-terminal? Thanks.

Amazing I can't find this but I must be googling wrong. I found shutdown, halt, reboot but not logout/logoff...searched users, sessions...

---

### Post by PmDematagoda on 2008-01-12
According to this old [thread]("http://ubuntuforums.org/showthread.php?t=529321"), this is the command:-
```
gnome-session-save --kill
```

---

### Post by mivadar on 2008-01-12
Have You tried

sudo skill -KILL -u yourownusername

---

### Post by jjsonp on 2008-01-12
Haven't tried the second one yet, but the first one works!

'gnome-session-save --kill'

I stumbled across this helpful hint: if you know the terminal command, type 'man' in front of it and that brings up the documentation ('manual') for that command.

So I typed:
'man gnome-session-save

and that displayed the '--kill' command along with all the other valid commands and usage.

---

### Post by jjsonp on 2008-01-12
Oh but you have to add the '--silent' option if you don't want to click the logout button.

---

