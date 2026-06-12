---
title: "Airplane Mode Function Key on UX31A Zenbook"
date: 2014-03-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Jacob_Gerlach on 2014-03-21
UX31A running 12.04

All function/multimedia keys worked out of the box except the airplane mode/wifi key on F2. 

Has anyone found a solution to this?

---

### Post by TheFu on 2014-03-22
If you know the command to be run, you can map it to the F2 keyboard depending on the WM used.
If openbox, something like:
```
    <keybind key="F2">
       <action name="Execute">
        <command>pm-suspend </command>
      </action>
    </keybind>

```
works for suspending a system (if a few things are setup).

---

### Post by Jacob_Gerlach on 2014-03-25
I am trying to bind to Fn+F2, not F2.

After some further research, I discovered that I can find a key code using:

```
sudo showkey -k
```
Which shows me that the system is not even recognizing Fn+F2 as a unique keypress.

This combination is recognized in Windows, so I don't think it's a BIOS problem, but I don't know where to go from here.

---

### Post by TheFu on 2014-03-25
**man -k keyboard**
will show a list of other keyboard related tools.
I was looking for the standard X/Windows keyboard tool - didn't see it on my system. Sorry.

Don't know if Fn-F2 can be handled by the WM.

---

### Post by TheFu on 2014-03-25
another forum error. double-post.

---

