---
title: "Package Manager where is it installed"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by turbo63 on 2006-01-16
Ok I used Package Manger to install some programs but now I can't figure out how to run them.  They are not under applications or anything.  I installe 3d chess and GNUcash.

Thanks!
Kevin

---

### Post by Double A Ron on 2006-01-16
Have you looked in your /bin or /usr folder?  There might be an executable file in one of those folders.

---

### Post by jsmidt on 2006-01-16
They are probably in you /usr/bin directory.

Go into a terminal type
```

cd /usr/bin

```

then type 
```

ls

```

A bunch of programs will pass by.  Find the one you installed.  Let say it is called mozilla.  Run it by typing:
```

./mozilla

```

Now if you want the program in your menus go to "Applications Menu editor" in under APPLICATION->SYSTEM TOOLS

Open it up.  

Go to where you want it.  Click on "new entry" type this in the "command slot"
```

/usr/bin/mozilla

```

Now it should be in your menu.  Click on it and it should run. :)

---

### Post by goatflyer on 2006-01-16
after installing things with synaptic, open a terminal window and type:

$ which 3dchess

and

$ which gnucash

Now you'll know where your next install gets installed.

---

### Post by Sef on 2006-01-16
If you do Alt+F2, the run application box comes up.  Just type the name of the program and it runs.  It is case sensitive, so the wrong case will give you a wrong answer.  E.G., typing Firefox (with capital F) will give you this:
```
Cannot display location 'file://Firefox' Details: There is no default action associated with this location.
```   But by typing firefox (small caps), click run and it will start up.

---

### Post by aysiu on 2006-01-16
Alt-F2 ```
3Dc
```

---

