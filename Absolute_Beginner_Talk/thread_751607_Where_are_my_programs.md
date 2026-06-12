---
title: "Where are my programs?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by PFSpectrum on 2008-04-10
I just installed blender and i need to find the folder where it is installed. In windows programs installed to C:\program files. Where is the default install for ubuntu? or at least where is the default instal for blender?

---

### Post by Oldsoldier2003 on 2008-04-10
> **PFSpectrum said:**
> I just installed blender and i need to find the folder where it is installed. In windows programs installed to C:\program files. Where is the default install for ubuntu? or at least where is the default instal for blender?

```
which blender
whereis blender
```

Usually programs install to /usr/bin but it really depends on who packaged the program and if they followed the Ubuntu/debian packaging guidelines.

---

### Post by tamoneya on 2008-04-10
there should be a bunch of stuff in /usr/lib/blender.  Remember though that in order to run it all you need to do is type "blender" into terminal

---

### Post by bodhi.zazen on 2008-04-10
> **tamoneya said:**
> there should be a bunch of stuff in /usr/lib/blender.  Remember though that in order to run it all you need to do is type "blender" into terminal

```
locate blender
```

Will find it all, if you recently installed though you need to update the database first

```
sudo updatedb
```

---

### Post by PFSpectrum on 2008-04-10
thanks guys =]

---

### Post by brian_p on 2008-04-10
> **PFSpectrum said:**
> I just installed blender and i need to find the folder where it is installed. In windows programs installed to C:\program files. Where is the default install for ubuntu? or at least where is the default instal for blender?

```
dpkg -L blender
```

gives a list of all the files and their locations.

---

### Post by MrFSL on 2008-04-10
Check under the sink. ... Thats where I keep my blender ;)

---

### Post by Laser Dude on 2008-04-10
You shouldn't need to access your program's folder for anything.  That's a problem with Windows.  You should be able to do whatever you need to do without directly opening that folder.  If you just want to open blender, then just typing "blender" into a terminal will work (like has been said), or if there isn't a link on your Applications Menu, then you can right click the menu, click "edit menus", and click "new item", and write "blender" in the "command" area.

If you're trying to do something other than running the program, then let us know.

---

