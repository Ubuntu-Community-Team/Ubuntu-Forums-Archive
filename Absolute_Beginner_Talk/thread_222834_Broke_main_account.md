---
title: "Broke main account"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by c2s on 2006-07-25
I somehow manage to break something in the main account that is made when you install. I am when I right or left click the desktop nothing happens. I can add or remove things to the taskbar and they do run. I figured out how to add another user and that desktop works but doesn't have permission to do much. Is how do I add "sudo?" permission to that account or is there any idea what I did to the 1st account. And help would be greatly appreciated. And I am a beginner all of 15 minutes experience before I went and broke it so I need everything laid out in very plain talk. On the plus side the install went great.

---

### Post by aysiu on 2006-07-25
**Fix your account**:
Paste these commands into the terminal. ```
mv ~/.config ~/.config.old
mv ~/.xfce ~/.xfce.old
``` Then log out and log back in again.

**Give the new account *sudo* permission**:
```
sudo adduser *newusername* admin
```

The terminal is at the top of the XFCE menu. If the menu doesn't work, press Control-Alt-F1, log in, and you'll have a virtual terminal where you can type those commands.

---

### Post by c2s on 2006-07-25
Thanks will try. :-P

---

### Post by c2s on 2006-07-25
Update

```
mv ~/.config ~/.config.old
```
Went fine

but
```
mv ~/.xfce ~/.xfce.old
```
Gave me this error:
```
mv: cannot stat '/home/c2s/.config' :no such file or directory
```

But the main login seems to work fine now. Is the second part important? 

And How do I relog into the gui from the promt?

---

### Post by aysiu on 2006-07-25
Press Control-Alt-F7

---

### Post by c2s on 2006-07-25
Thank you. For all the help :cool:

---

