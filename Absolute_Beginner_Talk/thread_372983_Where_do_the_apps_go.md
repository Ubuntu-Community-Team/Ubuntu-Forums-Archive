---
title: "Where do the apps go?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Qwertinsky on 2007-02-28
Where do application go when they are installed. For instance I just installed Xmacro using the Synaptic package manager.

 It does not show up in any of the menus.

Now I am stuck looking trough each and every directory manually looking for it, 

There has to be an easier way ](*,) 

The search in the File Browser does not seem to work very well...

---

### Post by Maestro23 on 2007-02-28
Apps installed via Synaptic, apt-get/aptitude are stored in:

[COLOR="Red"]/usr/bin[/COLOR]

---

### Post by highneko on 2007-02-28
Try this command:
```
dpkg -L Xmacro
```

---

### Post by x1a4 on 2007-02-28
Xmacro is a package which installs a few **scripts**--not a software application.  It's not in the menu because it shouldn't be.  

All xmacro scripts are in */usr/bin* and they are 

[I]/usr/bin/xmacroplay-keys 
/usr/bin/xmacrorec2 
/usr/bin/xmacroplay 
/usr/bin/xmacrorec [/I]

Be sure to read the entire description of a package before installing.

See the following for info on directory structures

[http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)

---

