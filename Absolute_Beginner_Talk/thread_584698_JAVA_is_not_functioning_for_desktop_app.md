---
title: "JAVA is not functioning for desktop app"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by gonzaloclavell on 2007-10-21
Hi , i have installed squirrel sql, but when it starts ups only shows a grey window. It seems a problem with java AWT and Swing. I tried with all versions of java jdk and nothing changed.
I tried with other Desktop Java Apps and failed the same way.
Well , i hope somebody could tell me something about that 
thanks

---

### Post by luisromangz on 2007-10-21
Are you running Compiz? If so, deactivate it before running Java apps. Swing is piece of crap, it doesn't behave as it should to be compatible with Compiz.

---

### Post by gonzaloclavell on 2007-10-21
I dont know what compiz is and hot to stop it ...
please if somebody could especify me how run java desktops apps in ubuntu , please ,,... for dummies ...
Thank you very much

---

### Post by manningr on 2007-11-27
I believe you will find that it is called "Desktop Effects" and is accessed from the 
System -> Preferences -> Desktop Effects menu sequence.

Rob

---

### Post by jordanmthomas on 2007-11-27
Here's how you can fix this while keeping your desktop effects:
press alt + f2 and type this:
```
gedit ~/.bashrc
```
Type (or copy and paste) this into that file.
```
export AWT_TOOLKIT=MToolkit
```
save it and close it.

Then, log out and back in and java programs should work.

---

