---
title: "how to terminate 3D game"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by dronepower on 2006-07-10
I do know how to force termintating non 3D applications, but I wonder how to do that with 3D games (in case they freeze or something)

---

### Post by asterisc on 2006-07-10
Hi,

look, you can do that by following the sequence:

- Press Alt + F1 (to switch to a console)
- log in 
- ps auxww | grep appName
- kill -9 pid
- exit (to log out)
- Press Alt + F7 (switch to X)

Hope that helped

---

### Post by Jucato on 2006-07-10
> **asterisc said:**
> Hi,

look, you can do that by following the sequence:

- Press Alt + F1 (to switch to a console)
- log in 
- ps auxww | grep appName
- kill -9 pid
- exit (to log out)
- Press Alt + F7 (switch to X)

Hope that helped

Just a few corrections/additions
-it's Ctrl+Alt+F1
- using ps auxwww | grep *name_of_your_app*, the PID (process ID) of the app you are trying to kill will be in the second column of the output
- Ctrl+Alt+F7 to switch back to X (the GUI)

---

### Post by 3rdalbum on 2006-07-10
Quicker way:

1. Control-Alt-F1 to switch to a terminal.
2. Log in
3. Type:
```
pkill appName
```
4. Control-Alt-F7 to switch back to X.

---

### Post by dronepower on 2006-07-11
mmm I tried to kill unreal tournament this way.

but everytime I try to kill ut2004-demo the way you described the PID changed.

- ps auxww | grep appName
- kill -9 pid

I just can´t kill the damn game :o 

with the pkill command I won´t work as well. Has this something to do with unreal tournament?

---

### Post by Jucato on 2006-07-11
how about trying
> killall *appName* instead?
and appName is what the the app is called when you do ps aux

---

### Post by FuzZy2006 on 2006-07-11
If a game freezes, it freezes, there's nothing you can do. I think that in such a case the keyboard is disabled. Try to activate/deactivate NumLock or CapsLock and see if those lights are changing. In my case - NO!

---

### Post by Jucato on 2006-07-11
As long as the keyboard is responding/functional, you can still get out of a freeze without restarting the whole system. Unfortunately, you would still have to restart X by pressing Ctrl+Alt+Backspace.

---

